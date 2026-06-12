---
title: "gnome-sound-recorder"
date: 2016-11-07
forum: MINT
---

### Post by borgward on 2016-11-07
Where do I find earlier versions of gnome-sound-recorder? How do I install them, apt-get install? I presently have 3.18.2 installed in Cinnamon 18. It does not have the features that the earlier version had that I was using with Cinnamon 17.

---

### Post by ajgreeny on 2016-11-08
This does not answer your specific problem about gnome-sound-recorder versions but I suggest you have a look at **audio-recorder** as a replacement.

Have a look at [https://ubuntuforums.org/showthread.php?t=2295381](https://ubuntuforums.org/showthread.php?t=2295381) where you can see how to get it; I've been using it for some time now with no problems, and find it terrific for the more simple recordings that I do.  If I need something for more intricate recording I use audacity.

---

### Post by borgward on 2016-11-14
> **ajgreeny said:**
> This does not answer your specific problem about gnome-sound-recorder versions but I suggest you have a look at **audio-recorder** as a replacement.

Have a look at [https://ubuntuforums.org/showthread.php?t=2295381](https://ubuntuforums.org/showthread.php?t=2295381) where you can see how to get it; I've been using it for some time now with no problems, and find it terrific for the more simple recordings that I do.  If I need something for more intricate recording I use audacity.

How do I install audio-recorder in mint 18 Cinnamon? What version to use? Where to find it?

~ $ sudo apt-get install Audio-recorder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package Audio-recorder

---

### Post by howefield on 2016-11-14
Assuming that you have added the ppa details and updated your sources, the package is not capitalised..

```
sudo apt-get install audio-recorder
```

---

### Post by borgward on 2016-11-14
> **howefield said:**
> Assuming that you have added the ppa details and updated your sources,

How do I add the ppa details and update the sources

 > **howefield said:**
> the package is not capitalised..

```
sudo apt-get install audio-recorder
```


~ $ sudo apt-get install audio-recorder
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package audio-recorder

---

### Post by howefield on 2016-11-14
The information is contained in the link ajgreeny has posted above, but essentially is

```
sudo add-apt-repository ppa:audio-recorder/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install --reinstall audio-recorder
```

---

