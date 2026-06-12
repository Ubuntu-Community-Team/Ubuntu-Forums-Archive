---
title: "Can I install ubuntu to vmware while in ubuntu?"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by BLTicklemonster on 2006-11-24
I want to test out edgy, but don't care to mess with any of my physical drives. So I came up with a solution, maybe. I want to install edgy in vmware server, and have tried it with the live cd, but it hangs at 15 percent install (detecting file systems). I just got the edgy iso, and tried it, and it, also hung up at 15 percent install. 

I set the virtual drive to be an ubuntu drive, and boot from the iso. I let the partitioner do it's thing automagically, too. I can't think of anything else I need to be doing.

Is there a way to install edgy on vmware in edgy?

---

### Post by aysiu on 2006-11-24
I don't know about VMWare Server, but you can certainly test it out in VMPlayer (which is in the repositories). [This tutorial](http://www.linuxforums.org/applications/using_vmware_player_to_test_linux_distributions.html) really helped me out.

---

### Post by BLTicklemonster on 2006-11-24
Aysiu, you totally rock, did you know that? If not, you do. Thanks.

---

### Post by BLTicklemonster on 2006-11-24
whoa, just tried installing from synaptic, and seeing as how I already have vmware server, I'm not sure how to answer the questions. I think I'll wait for some guidance...

---

### Post by aysiu on 2006-11-24
There are basically three things you need:
edgy.vmdk, which is the fake hard drive VMWare will use
edgy.vmx, which is the configuration file VMWare will use
edgy.iso, which is the disk image you'll use to install Edgy on .vmdk

---

### Post by BLTicklemonster on 2006-11-24
Well, that's going to have to wait, regardless. Player would not install, it says there's something broken, and Server will not work now. I have an update pending because I have Player half way installed now. Soooo, I'm kind of messed up here. I can't remove player using synaptic because I get this error

```
E: vmware-player: subprocess pre-removal script returned error exit status 2
```

So I need to drop back and reevaluate things.

---

### Post by BLTicklemonster on 2006-11-26
After trying again, and getting nowhere, I went off in another direction doing something else, and wanted to install something (without thinking about the broken link from an unsuccessful install of player...) and installed with aptitude, and guess what? aptitude gave me an easy out on removing player. I just redid my server distrib, and all's well. 

Now those packages you mention are for player only, right? Or for server, too?

---

### Post by aysiu on 2006-11-26
I've never used Server before, so I don't know.

All I know is that's how I get VMWare working on Player--I create those three files and run *vmplayer* and point it to the .vmx file.

---

### Post by BLTicklemonster on 2006-11-26
You know, you may be right. I just looked in my vmware folder, and the files are in there. I'll boot back to edgy (icewm in dapper is better than in edgy. I can't remember what all I did to it to make it the way it is, so I keep booting to dapper to run icewm) and set that all up and try it later. Thanks again aysiu.

---

