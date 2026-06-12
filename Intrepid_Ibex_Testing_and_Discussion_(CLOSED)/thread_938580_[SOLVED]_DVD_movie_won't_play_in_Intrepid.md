---
title: "[SOLVED] DVD movie won't play in Intrepid"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Zzzach on 2008-10-05
I'm trying to watch the x-files on dvd and none of my video programs will open the dvd (VLC, totem, mplayer). I have restricted extras installed. Is there something I need to download to get dvds to play on intrepid or do you think the x-files season dvd has some sort of protection on it? :confused:

---

### Post by wolfen69 on 2008-10-05
are you sure libdvdcss2 got installed? in intrepid, there was no flash or java in the repos.
 install the medibuntu repos and ```
sudo apt-get install libdvdcss2
```

---

### Post by dewfiend23 on 2008-10-05
i'm running intrepid as well, and that fix didn't work wolfen, it shot out this:
```
mclovin@mclovin-desktop:~$ sudo apt-get install libdvdcss2
[sudo] password for mclovin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

```

any thoughts?

---

### Post by xc3RnbFO8P on 2008-10-05
Read this:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Zzzach on 2008-10-06
Thanks for the help! I think that will work :popcorn:

---

### Post by Gina on 2008-10-20
I've read the medibuntu page and added and installed as described but Totem still gives an error.

I'm trying to play a DVD I recorded myself so there's no protection.  Any help greatly appreciated :)

---

### Post by rockin_goliath on 2008-10-20
You are probably getting errors due to this bug:
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/260765]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/260765")

I am also having some major DVD playing issues. If these problems aren't fixed in time, I would recommend using VLC until things clear up upstream.

---

### Post by Gina on 2008-10-22
Thank you :)  I'll try VLC.

---

