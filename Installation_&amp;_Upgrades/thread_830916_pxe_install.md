---
title: "pxe install"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by rosslev on 2008-06-16
I'm trying to install hardy from a windows box using pxe as my computer has no cd-rom.

I have followed the guide here;
[http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)

but the installation stops at a red screen with the following error;

'failed to load installer component - loading kickseed-common failed for unknown reasons. aborting.'

here is is a pic of the error;


[IMG]http://bp0.blogger.com/_jXBmTH6W1Es/SFZp2HHUsfI/AAAAAAAAAAc/WzT596eX7vE/s320/image-upload-112-744201.jpg[/IMG]


I have managed to do this before, on the same pc but an older ubuntu release without probs, anyone have any ideas, I tried a different mirror but get the same error?

Ross.

---

### Post by Partyboi2 on 2008-06-17
[[COLOR=Blue]Unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/") works well if you don't have a cdrom. Maybe try that and see if you are able to get further with installing.

---

### Post by Paul Weaver on 2008-06-17
> **rosslev said:**
> I'm trying to install hardy from a windows box using pxe as my computer has no cd-rom.

I have followed the guide here;
[http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)

but the installation stops at a red screen with the following error;


It's a known bug that was introduced a few days ago. 
[http://ubuntuforums.org/showthread.php?t=824576](http://ubuntuforums.org/showthread.php?t=824576)
Only solutions at the moment are

1) Contine regardless, <Continue>, <Continue>, Download Installer Components, <Continue>
2) to use the beta version of 8.04.1 (I did this succesfully), 
3) wait for the final version of 8.04.1 and hope no more regressions happen
4) go back to using gutsy. 

I'm pretty annoyed by it, but then I guess as I don't pay for a support contract yet I don't have a lot to moan about :)

---

