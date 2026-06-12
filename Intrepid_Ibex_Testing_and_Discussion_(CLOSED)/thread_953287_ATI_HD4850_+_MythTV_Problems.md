---
title: "ATI HD4850 + MythTV Problems"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by w0ng on 2008-10-20
I'm Running Ubuntu Intrepid Ibex 8.10, using the latest fglrx video drivers. Comp specs are listed in my sig.

My TV tuner is the DigitalNow TinyTwin DVB-T Receiver: 
[http://digitalnow.com.au/product_pages/TinyTwin.html](http://digitalnow.com.au/product_pages/TinyTwin.html)

I have installed the appropriate Intel chipset drivers for linux from:
[http://linuxtv.org/hg/~anttip/af9015/rev/86a15e6b2d89](http://linuxtv.org/hg/~anttip/af9015/rev/86a15e6b2d89)

In both Windows XP SP3 and Windows Vista Business SP1 (without Aero), everything works perfectly using the provided DNTV Live! software - scanning, viewing, PinP, recording, etc.

I am able to scan for all the available (Sydney, Australia) SD and HD stations that I receive on my Windows Vista Business SP1 partition.

Problem 1: Starting both mythfrontend and mythtv-setup, the whole image is blocky, distorted, out of sync and unreadable
Temporary workaround: start mythtv in an unstandard resolution e.g. "mythfrontend -geometry 1080x1049". This displays the image normally (albeit not in fullscreen mode)

Problem 2: Cannot detect dual channels in mythtv-setup. For "DVB Device Number", "0" is the only number listed
[[img]http://img129.imageshack.us/img129/1539/36216955tp2.th.jpg[/img]]("http://img129.imageshack.us/my.php?image=36216955tp2.jpg")[[img]http://img129.imageshack.us/images/thpix.gif[/img]]("http://g.imageshack.us/thpix.php")

Problem 3: When I first press "Watch TV", Images are displayed in split screen (same image displayed at the top and bottom).
[[img]http://img518.imageshack.us/img518/2241/58718157hi8.th.jpg[/img]]("http://img518.imageshack.us/my.php?image=58718157hi8.jpg")[[img]http://img518.imageshack.us/images/thpix.gif[/img]]("http://g.imageshack.us/thpix.php")

Problem 4: When I change channels (up/down -> Enter), the channels become distorted in a manner similar to one of the screenshots below (audio is fine).
[[img]http://img162.imageshack.us/img162/8667/32957103te5.th.jpg[/img]]("http://img162.imageshack.us/my.php?image=32957103te5.jpg")[[img]http://img162.imageshack.us/images/thpix.gif[/img]]("http://g.imageshack.us/thpix.php")[[img]http://img162.imageshack.us/img162/6180/64511115np2.th.jpg[/img]]("http://img162.imageshack.us/my.php?image=64511115np2.jpg")[[img]http://img162.imageshack.us/images/thpix.gif[/img]]("http://g.imageshack.us/thpix.php")

I have tried modifying /etc/X11/xorg.conf per recommendations @ [http://www.mythtv.org/wiki/index.php/AtiProprietaryDriver](http://www.mythtv.org/wiki/index.php/AtiProprietaryDriver) with no success

Similar bugs have been noted @ [http://ati.cchtml.com/buglist.cgi?quicksearch=mythtv](http://ati.cchtml.com/buglist.cgi?quicksearch=mythtv) with no responses

Can somebody recommend fixes to any of the listed problems?

---

### Post by w0ng on 2008-10-20
Temporary fix for me is this:
Alt+F2 > mythfrontend -geometry 1680x1049 > TV Settings > Playback > Next > Next (i.e. Playback Profiles (3/9))
Changed "Current Video Playback Profile" to "CPU++"
"if rez > 0 0 -> ffmpeg & XVideo" > Edit
Change "Decoder" from "Standard" to "libmpeg2"
Change "Max CPUs" from "1" to "4"
Keep pressing Next/Finish until your back into the main menu screen

Using libmpeg2 decoder, I am able to view and switch between all standard definition channels without the screen being split into 2 and without the images being distorted. The video still suffers from interlacing and image tearing, but at least it's watchable from a 22" computer monitor. However, whenever I switch to any HD channels, the image distortion occurs again. Hence, I made all HD channels invisible via mythtv-setup.
[[img]http://img366.imageshack.us/img366/8415/screenshot1xq9.th.jpg[/img]]("http://img366.imageshack.us/my.php?image=screenshot1xq9.jpg")[[img]http://img366.imageshack.us/images/thpix.gif[/img]]("http://g.imageshack.us/thpix.php") [[img]http://img233.imageshack.us/img233/581/screenshot2eu9.th.jpg[/img]]("http://img233.imageshack.us/my.php?image=screenshot2eu9.jpg")[[img]http://img233.imageshack.us/images/thpix.gif[/img]]("http://g.imageshack.us/thpix.php") [[img]http://img233.imageshack.us/img233/4570/screenshot3qv8.th.jpg[/img]]("http://img233.imageshack.us/my.php?image=screenshot3qv8.jpg")[[img]http://img233.imageshack.us/images/thpix.gif[/img]]("http://g.imageshack.us/thpix.php") [[img]http://img366.imageshack.us/img366/1585/screenshot4vb1.th.jpg[/img]]("http://img366.imageshack.us/my.php?image=screenshot4vb1.jpg")[[img]http://img366.imageshack.us/images/thpix.gif[/img]]("http://g.imageshack.us/thpix.php")

---

