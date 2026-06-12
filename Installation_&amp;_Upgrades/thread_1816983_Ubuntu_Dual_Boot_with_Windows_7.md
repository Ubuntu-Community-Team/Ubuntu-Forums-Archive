---
title: "Ubuntu Dual Boot with Windows 7"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by PyroboyUK on 2011-08-02
Hello, 

Im trying to install Ubuntu 11.04 on my Acer 5750 (i3) that i have just received today. Im not sure what im doing wrong but i thought i would try for some advice before i attempt a third install as i must be doing something wrong. 

As the laptop stands Windows 7 is the main OS however i would like to have the option to boot into Ubuntu to use for the majority of the time. 
I have set a 2gb portion for Swap Space and 60gb that was set too "/", i thought you set it as boot in the formatting menu however it does not let me proceed without setting my 60gb portion too "/". 

So the install goes with no issues and asks me to restart, the problem is that every boot sequence goes straight into Windows without even detecting a Linux install.

Is there anything major i am missing?

Thanks

---

### Post by oldfred on 2011-08-02
Somewhere you are not getting grub installed to the MBR. 

Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by tommcd on 2011-08-03
> **PyroboyUK said:**
> 
I have set a 2gb portion for Swap Space and 60gb that was set too "/", i thought you set it as boot in the formatting menu however it does not let me proceed without setting my 60gb portion too "/". 

I you are only creating 2 partitions, then one needs to be root. The other can be swap.
So just install Ubuntu again. Let the installer create root and swap partitions. The installer should automatically install grub to the master boot record so you can boot either Windows7 or Ubuntu.

---

