---
title: "Activating graphics on the Intel  i7 ivy bridge DELL Presicion M4700"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by willemferguson on 2012-11-13
Activating the graphics of the DELL Presiciom M4700
 
 Most of the DELL Precision M4700 series of laptops implement the new i7 Intel Ivy Bridge CPU and associated circuitry. This includes two graphics systems, a [[COLOR=Blue]buit-in Intel Graphics processor[/COLOR] ]("http://www.notebookcheck.net/Intel-HD-Graphics-4000-Benchmarked.73567.0.html")(GPU) for low-resolution graphics, and a separate high-end GPU for use in graphics applications such as CAD, GIS and games. In order to save laptop battery power, the built-in GPU is used by default and the more power-hungry NVIDIA system is activated only when needed. Applications need to know which graphics interface to use. One of the high-end GPUs used by Dell is the [[COLOR=#0000ff]NVIDIA Quadro K1000M [/COLOR]]("http://www.notebookcheck.net/NVIDIA-Quadro-K1000M.76894.0.html")[COLOR=#000000]graphics system[/COLOR][COLOR=#000000]. [/COLOR] NVIDIA have designed an automatic switching system to switch between these two graphical subsystems, termed the [[COLOR=#0000ff]Optimus technology[/COLOR]]("http://www.nvidia.com/object/optimus_technology.html").  The Optimus technology has not been ported for Linux. However, an open source project has been initiated to create the infrastructure for automated graphics switching, called the [[COLOR=Blue]Bumblebee projec[/COLOR]t]("http://bumblebee-project.org/"). NVIDIA have_[COLOR=Blue] [COLOR=Blue][promised]("http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY")[/COLOR][/COLOR] _to provide Optimus for Linux, but the technology is not yet available for Linux.

 In order to get the Dell Precision M4700 working, one needs to perform at least three steps:
 1) Activate Optimus technology in the BIOS settings. Currently it explicitly says “Only for Windows 7 installations”. Override this setting and activate the Optimus technology.
 2) If necessary, install the Intel GPU driver. This should allow access to the basic system.
 3) Install the Bumblebee software. It should not be necessary to install a NVIDIA driver, since Bumblebee will provide the appropriate graphics driver for the NVIDIA card.
 
 Software that need graphics acceleration are run from the command line using the "optirun" command. For example:
 
 optirun google-earth

---

