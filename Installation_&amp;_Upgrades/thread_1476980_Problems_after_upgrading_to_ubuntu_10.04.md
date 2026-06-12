---
title: "Problems after upgrading to ubuntu 10.04"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by gabibl on 2010-05-08
Hello, 

Yesterday my ubuntu asked if I would like to upgrade to ubuntu 10.04 (I had 9. something). I agreed with the upgrade, but after rebooting the computer I am having some problems. The most inconvenient problem is that I have _**no sound**_. I have tried installing gnome-alsamixer, but that has not worked. I am also receiving a message at boot "An error occurred while mounting /opt/windows/". I have windows a and ubuntu on my computer. Can anyone help me? Specially with the_** sound problem**_..

---

### Post by mörgæs on 2010-05-08
I could be wrong, but from the bean count I guess that you are a beginner, so I would recommend the easy approach: If 9.10 was working fine, just backup your files and do a clean install. Takes one hour, and you have the proof that it works. 

9.10 is supported a year from now, so there is no rush to look for alternatives.

---

### Post by gabibl on 2010-05-08
Hi, I am a beginner so I'm very unsure about reinstalling ubuntu from scratch. Apart from that, I am not sure if I had 9.10 or 9.04. But ubuntu was working fine and now that I upgraded to 10.04 I have many problems. I have partially solved the sound problem, but my firefox still has no sound. I am having problems with my latex, it turns out that revtex4 has been substituted by revtex4.1, which is not working properly (for example it does not understant the \footnote command). Apart from that, I keep getting the error message I mentioned and other error messages while booting. I am also having problems with my skype, which suddenly closes when I try to use its chat. Is there no way to "downgrade" to 9.10 without having to reinstall ubuntu?

---

### Post by holzweaver on 2010-05-08
I've also been having some problems with my upgrade. I had the sound issue but that was fixed when i went into my sound preferences and changed my output connector to analog speakers which used to be my default. Hopefully that helps you. I'm now trying to work on some issues with flash video.... sigh...

---

### Post by mörgæs on 2010-05-09
10.04 is not the best option on all hardware. If 9.04 or 9.10 works better, then just use them and let 10.04 mature for a few more months. Best is to try a live CD boot as a first step.

Here is a support chart:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

There is no option of downgrading other than a clean install (which I would recommend anyway, also for upgrades).

You can download the various releases here:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)


Edit: And by the way, don't worry about installing from scratch. It is far easier than repairing a system.

---

### Post by yanncarlier on 2010-05-09
Hi

After upgrading to 10.04 I have no Sound

#####################################################

oot@yannwho:/home/yanncarlier/Desktop# ./alsa-info.download
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See './alsa-info.download --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=08be32cceb8bcfb1aaea12cbcd01b18ded5fb629](http://www.alsa-project.org/db/?f=08be32cceb8bcfb1aaea12cbcd01b18ded5fb629)

Please inform the person helping you.

root@yannwho:/home/yanncarlier/Desktop# 


root@yannwho:/home/yanncarlier/Desktop# uname -a
Linux yannwho.xxxxxxxxx.com 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

###################################################3

Help thanks

---

