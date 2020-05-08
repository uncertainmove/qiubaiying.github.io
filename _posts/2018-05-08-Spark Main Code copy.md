---
layout:     post
title:      Spark Main Code
subtitle:   分布式计算平台 Spark 主函数调用
date:       2018-02-01
author:     UNMOVE
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - Spark
    - Code
    - Distributed Computing
---

# Main Code

class DenseVectorV
extends Vector[V] {
def this(data: Array[V]) = this(data, 0, 1, data.length)
…
}
class LabeledPoint(var label: Double, var features: Vector[Double])

val lines = sparkContext.textFile(inputPath)
val points = lines.map(line => {
val features = new ArrayDouble
…
new LabeledPoint(new DenseVector(features), label)
}).cache()
var weights = DenseVector.fill(D){2 rand.nextDouble - 1}
for (i <- 1="" to="" iterations)="" {="" val="" gradient="points.map{p" =="">
p.features (1 / (1 + exp(-p.label weights.dot(p.features))) - 1) p.label
}.reduce(_ + _)
weights -= gradient
}