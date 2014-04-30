# PixiePlot

[Download](https://github.com/draftomatic/wildstar/blob/master/lib/PixiePlot.lua)

> Package = Apollo.GetPackage("Drafto:Lib:PixiePlot-1.4").tPackage 

PixiePlot is a plotting library for WildStar. It can currently create line, stem, bar/histogram, scatter, polar, and parametric plots.


The Basics

First, get PixiePlot into your addon by using Apollo's Package system, and initialize it with a container Window:
local PixiePlot = Apollo.GetPackage("PixiePlot-1.3").tPackage
self.wndMain = Apollo.LoadForm("MyAddon.xml", "MyForm", nil, self)
self.wndPlot = self.wndMain:FindChild("Plot")
self.plot = PixiePlot(self.wndPlot)

Now the data. PixiePlot plots "DataSets." A DataSet is an object containing an x-start value, and an array of y-values. The x-values are computed from a given x-start and x-interval.
local dataSet = {
  xStart = 0, 
  values = {0, 1, 1, 2, 3, 5, 8, 13, 21}
}
For scatter plots, values is an array of objects with "x" and "y" fields.

Each DataSet can have a different x-start, allowing you to shift certain DataSets. This is useful for creating piece-wise plots, or for plotting dataSets with different x-bounds (e.g. you are tracking NPC damage and a new enemy spawns midway through combat). The x-interval, however, must be the same for all DataSets:
self.plot:SetXInterval(xInterval)

Finally, add the DataSet to the plot and call Redraw:

    self.plot:AddDataSet(dataSet)
    self.plot:Redraw()


## Quick Links

1. <a href="#"></a>


## API Reference

-  **PixiePlot:New(wndContainer, tOpt)**

   Creates a new plot. Plots are drawn inside the Window `wndContainer`. `tOpt` is an optional table of plotting options, which must be complete.



###Options

PixiePlot keeps a set of options that it will use for plotting. Options are set using `PixiePlot:SetOption(strName, value)`.

