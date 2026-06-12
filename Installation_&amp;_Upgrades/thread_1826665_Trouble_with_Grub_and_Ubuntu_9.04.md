---
title: "Trouble with Grub and Ubuntu 9.04"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by Xmetalfanx on 2011-08-16
I have done quick searching and read a few tutorials in "fixing grub", but somehow am still running into hiccups. 

_Bottom Line_: Dvd Drive died in my toshiba laptop and it was replaced (not before tech for some reason reformatted the Win7 partition... which was 100% un-needed, but thats beside the point now.  I redid win7 (the tech installed vista) and am TRYING to "redo grub". 

_Facts_: The Slackware AND Ubuntu Partitions ARE STILL THERE and when i use SuperGrub Boot CD (which doesn't restore my grub by itself) to boot into slackware, i can see ALL THE CONTENT of both Linuxes still there including grub on ubuntu partition

(Tri-Boot: Ubuntu, Slackware, and WIn7)

I had it working for two years or so, SO i know this "setup" works fine. 

I am A) Trying to do this as simply as possible.  B) Trying to avoid the need to download a 800MB ISO (as seen for this issue on this forum) and trying not to have to reformat Ubuntu Partition (though I have the .Debs I have downloaded for it backed up ... all 1.7GB of them)

I have /dev/sda1 as win7, /dev/sda2 as Slack and /dev/sda3 as Ubuntu (which contains Grub Legacy)..

Every command I do seems to result in an error like "invalid command" or "invalid Execution format " (i think that second one is right) type errors

Thanks TO ANYONE to can point me in the right direction.  I compiled (awhile back) a few kernels for Slackware, but feel goofy that I cant figure what i this out (what i thought was going to be a "2 minute" fix) 

-Xmetalfanx

---

### Post by hansdown on 2011-08-16
Hi, Xmetalfanx.

Ubuntu 9.04 has reached end of life.

Would you consider downloading, and installing 10.04?

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by kaizokuroof on 2011-08-16
> **hansdown said:**
> Hi, Xmetalfanx.

Ubuntu 9.04 has reached end of life.

Would you consider downloading, and installing 10.04?

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Oh nice, productive post.... This helps how? - Let me retype what you just wrote:

Ohai, Ubuntu 9.04 has reached the end of it's life upgrade to the LTS that is almost exactly the same!

Ahem, now thats out of the way....

The  easiest way to "fix" grub would be booting into a live CD of Linux -  I'd use Ubuntu as it's probably the most user friendly and has an easy  GUI to navigate.

In a nutshell, you must boot into a live CD -  Reinstall/install Grub to your bootloader partion and make sure that  drive is set to boot first. 

Eg Reinstall on: /dev/sda3 -and make sure that drive  is set to boot first in your boot order.

Here is the documentation on Grub 2: [B][https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[/B]
Cheers dude.

P.S: What commands were you trying to run?

---

### Post by hansdown on 2011-08-16
Thanks for your post, kaizokuroof.

You seem to be the guru of the moment, so I cede the stage to you.:)

---

### Post by oldfred on 2011-08-16
Post boot script from liveCD. 9.04 was where they started to introduce grub2. You booted with grub legacy and then could chain boot to grub2. And then convert to grub2 if you wanted. This will tell us what you have.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

