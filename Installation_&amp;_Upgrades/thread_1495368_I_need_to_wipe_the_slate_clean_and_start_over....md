---
title: "I need to wipe the slate clean and start over..."
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by rainbowagent7 on 2010-05-28
Hi all. I'll get straight to the point, I need to wipe the slate clean on my computer and start from scratch. I have too many issues and school is just around the corner for me, I've got a huge workload and don't have time to find solutions to my problems right now.
     I recently upgraded to Lucid but that only escalated my woes. The simple fact is my machine is getting too old and it's time to upgrade everything, which won't happen until fall. So for now I simply want to downgrade to hardy because it will be supported until April next year and it is very stable, plus I think it is the release that my graphics card got a decent resolution on (ATI, need I say more?).
           I'm somewhat of a noob, but I've got my wits about me and have researched the forums for many hours to find solutions, but to no avail. I don't want to go into details about what issues I'm having, I just need to know how to remove **ALL **kernels off of Grub and start from scratch. Any links to comprehensive tutorials would be ideal, or if someone knows of anything else that will work, please throw me a bone! Thanks in advance.
      
     P.S. I love Ubuntu and am a lifer. The philosophy behind it as well as the community are supreme and will someday rule the universe, thanks to those who make it happen.


:guitar:

---

### Post by SlidingHorn on 2010-05-28
> **rainbowagent7 said:**
> I just need to know how to remove **ALL **kernels off of Grub and start from scratch. Any links to comprehensive tutorials would be ideal, or if someone knows of anything else that will work, please throw me a bone! Thanks in advance.
      
     P.S. I love Ubuntu and am a lifer. The philosophy behind it as well as the community are supreme and will someday rule the universe, thanks to those who make it happen.


:guitar:

I would run your install, and when you're finished installing your fresh version, run the following terminal command:

```
uname -r
```

Write down the output, as that's the kernel you are using at the time.  Make sure you want to stick with it!  

From there, you can load up Synaptic and search for linux-image and mark the kernels you don't want for removal.  Apply changes.  Afterward, you have grub update:

```
update-grub
```

and you should be all set!

---

### Post by wilee-nilee on 2010-05-28
You don't have to delete anything if your just doing a fresh install download the cd pop it in and install.
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)
Thed second link seems to be working but the 1st list gives you options of torrents or a sever close to you.

---

### Post by rainbowagent7 on 2010-05-28
Thanks for the info. Only one more thing, I will probably want to go with one of the kernels from Hardy to try and reverse some of my issues, or is that not a good idea?

---

### Post by wilee-nilee on 2010-05-28
> **SlidingHorn said:**
> I would run your install, and when you're finished installing your fresh version, run the following terminal command:

```
uname -r
```

Write down the output, as that's the kernel you are using at the time.  Make sure you want to stick with it!  

From there, you can load up Synaptic and search for linux-image and mark the kernels you don't want for removal.  Apply changes.  Afterward, you have grub update:

```
update-grub
```

and you should be all set!

Why would the kernels from Lucid still be in a fresh install?

---

### Post by wilee-nilee on 2010-05-28
> **rainbowagent7 said:**
> Thanks for the info. Only one more thing, I will probably want to go with one of the kernels from Hardy to try and reverse some of my issues, or is that not a good idea?

First you can't down grade your only option that I know of is to do a fresh install, you could pull off the stuff you can't afford to lose as long as it isn't distro-centric.

---

### Post by rainbowagent7 on 2010-05-28
Thanks also Wilee Nilee, my last reply was to Sliding Horn but you posted before I was done. In a nutshell I think my problems came from a kernel upgrade. Will it be beneficial to revert back to a previous one, or will it cause problems? And thanks for the links, but I have saved every version of Ubuntu since Dapper Drake.

---

### Post by wilee-nilee on 2010-05-28
> **rainbowagent7 said:**
> Thanks also Wilee Nilee, my last reply was to Sliding Horn but you posted before I was done. In a nutshell I think my problems came from a kernel upgrade. Will it be beneficial to revert back to a previous one, or will it cause problems? And thanks for the links, but I have saved every version of Ubuntu since Dapper Drake.

I'm not sure what you want really. As I read you have a upgrade to Lucid that isn't stable or working for you. The only thing I would suggest is using the kernel at the bottom of the list. I don't know when you upgraded and if you have more then one kernel.

You might post your problems and see if it can be fixed, but generally a fresh install of any distro that is still supported is the best thing to do. Many have no problems with upgrades, but from hardy to lucid I would never have upgraded, but I never do anyway.

A fresh install of Hardy using the whole hard drive will wipe everything off as far as using it again, this seems like the quickest, and easiest answer to the dilemma.

---

### Post by rainbowagent7 on 2010-05-28
Thanks for your help. I don't want to seem like a flake, but I've got to get to sleep. I will try a fresh install tomorrow and go from there. If I have any issues with the kernel I'll holla! maybe with some sleep I will be able to make a post in less than an hour! Thanks again for ya'lls time.

---

