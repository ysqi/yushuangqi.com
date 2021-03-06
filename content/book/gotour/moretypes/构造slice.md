---
book_chapter: "0310"
book_chapter_name: "构造slice"
book_name: Golang入门指南
date: "2016-02-26T17:46:24.8428222+08:00"
description: ""
disqus_identifier: book000103010
slug: "making-slices"
title: Golang入门指南-构造slice
codeurl: "https://wide.b3log.org/playground/79560c54adb9e7c8883f12e2b02b0b42.go"
---

slice 由函数 `make` 创建。这会分配一个全是零值的数组并且返回一个 slice 指向这个数组：

	a := make([]int, 5)  // len(a)=5

为了指定容量，可传递第三个参数到 `make`：

	b := make([]int, 0, 5) // len(b)=0, cap(b)=5

	b = b[:cap(b)] // len(b)=5, cap(b)=5
	b = b[1:]      // len(b)=4, cap(b)=4

```Go
package main

import "fmt"

func main() {
	a := make([]int, 5)
	printSlice("a", a)
	b := make([]int, 0, 5)
	printSlice("b", b)
	c := b[:2]
	printSlice("c", c)
	d := c[2:5]
	printSlice("d", d)
}

func printSlice(s string, x []int) {
	fmt.Printf("%s len=%d cap=%d %v\n",
		s, len(x), cap(x), x)
}

```

