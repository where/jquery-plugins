# jQuery.whereTables.js
***

## Introduction

**jQuery.whereTables.js** is a simple plugin designed to allow you to toggle the visibility of columns in a table. It is `colspan` aware but currently doesn't support `rowspan`. It is more to serve as an introduction to writing a certain type of jQuery plugin than anything else so I offer no guarantee this will work for you in production. It is intentionally over-engineered to demonstrate a few different ways of accomplishing some things in JavaScript and to encourage discussion with the goal of establishing a set of best practices.

For further detail and instructions on how to utilize this plugin, please see the [annotated source](http://where.github.com/jquery-plugins/). 

## Usage

This library must be included on your page after the jquery plugin. You can include both with:

````<script src="//ajax.googleapis.com/ajax/libs/jquery/1.6/jquery.min.js"></script>
<script src="path_to_library/jquery.wheretables.js"></script>````

You can initialize this library by calling `.whereTables()` on any elements you want to use it on. For example, to use this library on all tables with a class of `toggleColumns`, you would need to initialize it with:

````$('table.toggleColumns').whereTables()````

**Note**: Don't forget to wrap that call in `jQuery.ready` (or the `$(function(){})` shorthand method).

### Methods

There are currently three methods available:

* `hideColumn`: Takes the column number as a param (zero-index), hides that column.
* `showColumn`: Takes the column number as a param (zero-index), hides that column.
* `toggleColumn`: Takes the column number as a param (zero-index), toggles between hiding or showing that column.

Calling these methods takes on this format:

````$(element).whereTables('method-name',argument1, argument2,...,argumentN)````

To hide the third column (column `2` with a zero-index) on a `table` with an id of `example`, you might call:

````$('#example').whereTables('hideColumn', 2)````

### Events

Each time a column is shown or hidden, an event is emitted from the element `jQuery.whereTables` was called on. The events are:

* `showColumn.whereTables`: emitted when a column is shown with an argument of the zero-indexed column number.
* `hideColumn.whereTables`: emitted when a column is hidden with an argument of the zero-indexed column number.

If you wanted to listen for one of these events and, say, pop up an `alert` when a column on a `table` with an id of `example` is shown, you might write the following:

````$('#example').bind( 'showColumn.whereTables', function( event, index ){
	alert( index );
} );