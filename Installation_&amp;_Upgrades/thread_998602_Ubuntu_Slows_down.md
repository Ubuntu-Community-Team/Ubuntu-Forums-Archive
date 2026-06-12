---
title: "Ubuntu Slows down"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by ivikas on 2008-12-01
Hello all,

          I am using ubuntu 8.04 LTS Desktop.I have a netgear wireless adapter and i managed to get connected to internet via ndiswrapper.At first the internet speed was good.But gradually the internet speed slows down so does the application like open office,gedit..takes long time to load and open up.Some of my friends says that Linux in the long usage creates lots of temprorary files which is responsible for slow down.Again Hardy slows down due to "system hang up(application becomes grey scale)" and i also loses screen resolutions. This (1440 X 900)  is correct resolution for my system.Some times this changes and i don't know how to restore it.(Well i just creates a back up copies of X11 and restores it when resolution goes wrong.,sometime i get around and sometimes not,i don't even know whether it is right way to do.In my system there are lots of unnecessary services running,like "chaking batery state...(i presume this is for laptops").I don't know what exactly are the unnecessary services and how to shut it down without compromising on security and increasing system boot up time.Similarly i have 2 other hardy machine and mystem is completely updated.I want to set up my system in such a way that the two fresh installation will first seek to install package from my system[ [COLOR="Red"]/var/cache/apt/archives[/COLOR] ] and in case if there is no pacakage must connect to internet and download from it.Is there any way to accomplish this?

                      Please give me some help,any weblinks and any suggestions by which i can make ubuntu perform better on my machine.

Thanks in advance

---

### Post by cariboo on 2008-12-01
I don't think you should listen to your friends as they don't sound like they know what they are talking about. It sounds like you have a memory leak of some sort. When your system starts slowing down agian open a Applications-->Accessories-->Terminal and type:

```
top
```

This  will open a application that will show you the highest CPU and Memory usage, and note which  apllication is hooging all the ram and cpu cycles. See screenshot for an example.

Jim

---

