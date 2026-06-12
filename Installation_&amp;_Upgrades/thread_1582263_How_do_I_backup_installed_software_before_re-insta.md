---
title: "How do I backup installed software before re-installing?"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by aisajib on 2010-09-26
Hi everyone! I'm posting again for another problem I haven't found any convincing solution to yet.
   
  For absolutely no reason, I reinstalled my Ubuntu. It&#8217;s not a wubi installation; but it&#8217;s a full installation. It didn&#8217;t cause any problem like old xp days. I just reinstalled because I tried too many themes on that and the system appeared jammed. I could fix it; but I thought a plain reinstallation would be much less difficult.
   
  Now the problem is, after reinstallation, I have to install all software such as VLC, GIMP, and plugins for mp3 and video codecs. I did know that I would have to download them again. And I will download them shortly. But I want to know is there any way I can preserve the installer of those applications and plugins to use after a fresh reinstallation or upgrade to latest version (say 10.10 for example)?

Also, I want to back up all the system updates through update manager so that I am not asked to update (by downloading 200+ MBs) after fresh reinstallation.
   
  Please note that my internet connection is very slow and its bandwidth is limited to 3GB per month. I can buy more space but you know it&#8217;s costly here. That&#8217;s why I want a way to back up all the software, plugins and application installers for further use. I have DVD writer on my machine so if I have to write a disk I&#8217;m capable.
   
  Please advice. Thanks in advance.

---

### Post by howefield on 2010-09-26
> **aisajib said:**
> But I want to know is there any way I can preserve the installer of those applications and plugins to use after a fresh reinstallation or upgrade to latest version (say 10.10 for example)?

All your downloaded .deb package files will be stored in 

```
/var/cache/apt/archives/
```

Once downloaded, you could copy them over to a safe place, then copy back if needed.

---

### Post by xircon on 2010-09-26
I found this a while back, not tried it:

[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

---

### Post by aisajib on 2010-09-26
Last time I looked in the specified folder but there was nothing.

I had done a cleanup using Ubuntu Tweak, though, because I didn't want caches to fill up by system space (11 GB with 1 GB swap, wait, what's a swap? :( ).

---

### Post by howefield on 2010-09-26
> **aisajib said:**
> Last time I looked in the specified folder but there was nothing.

I had done a cleanup using Ubuntu Tweak, though, because I didn't want caches to fill up by system space (11 GB with 1 GB swap,

If you had cleaned the folder out, then yes, it would be empty. ;)


> wait, what's a swap?

From a google search
> Swap space is an area on disk that temporarily holds a process memory image. When physical memory demand is sufficiently low, process memory images are brought back into physical memory from the swap area on disk. Having sufficient swap space enables the system to keep some physical memory free at all times.

This type of memory management is often referred to as virtual memory and allows the total number of processes to exceed physical memory.

---

### Post by aisajib on 2010-09-26
OK, let's say I won't clean up before having them backed up. But what about system update? I mean, except applications and plugins, the Update Manager comes up after fresh installation to download and install system updates for Ubuntu. This update contains all the security updates. Is there any method to have them backed up before I re-install?


Is 1 GB swap enough?

---

### Post by SeijiSensei on 2010-09-26
Swap typically runs anywhere from 1-2x the size of your physical memory. If you enter hibernation mode on a laptop, Linux uses the swap area to store the image of your memory, so swap should be at least equal to physical memory if you use hibernation.

If you run the "top" command from a prompt, you'll see statistics on memory usage, both physical and swap.  Linux uses most available free physical memory to cache disk reads and writes, so you'll probably see a fairly small amount of "free" physical memory.  If your swap partition is nearly exhausted, then you might consider adding more.  While swap is usually placed in a separate partition on the disk during installation, you can [create a file on the regular file system and add that to swap]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/") as well. 

As for the security updates, they'll be stored in /var/cache/apt/archives as howefield says.  I'd be hesitant about using them to replace packages from a new distribution version, though, because they may be older than the new packages you've already installed.  On the other hand, for optional packages like GIMP that aren't already on your system, you can install the version from the archives.  It will get updated if necessary the next time you let the updater run.

With only 3 GB of downloads per month, even downloading a single distribution CD is going to eat up a quarter of that allocation in one go.  I'd consider trying to find some other Linux users (there must be some in Bangladesh, yes?) and work out a scheme to download a single CD and duplicate it amongst yourselves.  Perhaps there's a school or university nearby that might help?  I looked to see whether there is an Ubuntu [mirror]("https://launchpad.net/ubuntu/+cdmirrors") in your country, but there does not seem to be one.  However, I also stumbled across [this posting]("https://lists.ubuntu.com/archives/ubuntu-bd/2009-January/003161.html") from a mailing list that discusses Ubuntu usage in Bangladesh.  I'd subscribe to that if I were you.

Oh, to exit from top, hold down the Ctrl key and type "C".

---

### Post by aisajib on 2010-09-26
Thanks Sensei! 

About security updates: I'm not going to use security updates on a version that is the latest. I just want to back up all the security updates that were released ever since I downloaded the ubuntu image and burned it to a CD. Hope you get it. 

So, updates are also available in that archives folder?

I used to download Ubuntu versions in my computer until my mobile service provider stop unlimited data plan. Schools over here don't have Internet connection. Only a few of them have computers! Some colleges do have Computers. But universities have computer lab. But the speed is again slow. Can't download. I will have to try out on my friend's pc who would be interested in downloading this.

In Bangladesh, there is a growing community with open heart for linux and linux enthusiasts. If you understood Bangla, I could show you how big sites there are. A lot of people, with a dedicated organization named bdOSN (Bangladesh Open Source Network) is providing free support for anything linux. But who's gonna meet them in person for a CD! ;)

I'd better ask someone who uses broadband internet to download a copy for me. :)

Thanks for your reply, again.

---

### Post by drs305 on 2010-09-26
There is a relatively easy way to export and then import your installed package **lists** into APT/Synaptic via Synaptic.

Open Synaptic, then File > Save Markings. 
Set the path and filename.
Make sure to tick the "Save full state, not only changes" option in the lower left corner.
Note that the Desktop you see as a place to save the file is root's Desktop, not your own. To save it to your own home folder, navigate through "File System, home, your username".

Note: Save the file to a location that won't be formatted when you do your new install !

To import the list in your new install, Open Synaptic and then:
File, Read Markings...

Note this doesn't save customizations, just the basic installs.

**ADDED:** This does not prevent you from having to download the packages from the server.

---

### Post by aisajib on 2010-09-26
Thank you very much! I understood the process. Hope this works.

I'm okay with only basic installs. All I don't want is to download them again from the server.

---

### Post by nushbi on 2011-10-09
thanx  [[COLOR=#d40000]**howefield**[/COLOR]]("http://ubuntuforums.org/member.php?u=186490") n [[COLOR=#d40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945") for saving da trouble....  :guitar:

---

