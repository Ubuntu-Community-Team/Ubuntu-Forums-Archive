---
title: "Compiz settings not  working in 12.04 Precise"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by iniquiTrance on 2012-04-22
I just upgraded to precise pangolin 12.04 LTS. I installed compiz manually. When I enable things such as wobbly windows, or desktop cube in compiz, the settings don't take effect. When I reload Compiz, the checkmarks remain, yet they seem to have no effect. Any ideas are much appreciated.

---

### Post by j_zhill on 2012-04-29
I am also experiencing this problem. That is: I set a mouse activation for window scale. It functioned as expected. After reboot, the functionality didn't persist.

Looking in ccsm after reboot, the settings remained. I was able to restore the functionality by setting mouse activation to "none", then setting it back to the desired corner, then closing ccsm. The window scale behaviour then persisted until next reboot.

Any advice on how to make ccsm settings persist after reboot would be appreciated.

Thanks.

---

### Post by jamesisin on 2012-04-29
I too am unable to get any wobble in my windows...

---

### Post by MC Buntu on 2012-05-02
OK, So here's what I did to finally get it working. 
Open up CCSM -> General -> General Options -> Desktop Size

Horizontal Virtual Size 4
Vertical Virtual Size   1
Number of Desktops      4

Click on all the settings you desire , i.e Wobbly Windows, Rotate Cube, etc.

Log out, Log back in...Presto! (maybe)

Worked for me. Good Luck!

---

### Post by iniquiTrance on 2012-05-02
Ok this was the problem for me. 

Make sure that you're not running Ubuntu 2d. Run:

```
echo $DESKTOP_SESSION
```

In my case, this returned:

```
ubuntu-2d
```

My Dell XPS 14 apparently uses nVidia Optimus technology, and the stock Ubuntu drivers weren't allowing Ubuntu 3D to run. Hence, the 3D effects in Compiz ccsm weren't sticking/working. 

I rectified this by installing Bumblebee:

[http://bumblebee-project.org/](http://bumblebee-project.org/)

Now everything checks out ok.

---

### Post by chilloutmo on 2012-05-09
> **j_zhill said:**
> I am also experiencing this problem. That is: I set a mouse activation for window scale. It functioned as expected. After reboot, the functionality didn't persist.

Looking in ccsm after reboot, the settings remained. I was able to restore the functionality by setting mouse activation to "none", then setting it back to the desired corner, then closing ccsm. The window scale behaviour then persisted until next reboot.

Any advice on how to make ccsm settings persist after reboot would be appreciated.

Thanks.

I have exactly the same problem. I set active corners for window scale and show desktop reboot, and they don't function anymore. But when I go to ccsm the settings are alright but to make them work I have to unselect them and reselect them again, only then they work. Only until the next reboot of course...

Any help?

I have a Asus 1215n with bumblebee installed and working fine. I never had any issues in 11.10 and compiz effects worked fine. I did not upgrade to 12.04 but did a fresh install. I tried putting the command compiz --replace in the startup applications and while it worked once it did not afterwards so I am back to square 1. 

Thanks,

chilloutmo

---

### Post by ranger1021994 on 2012-06-23
Even i cannot enable effects... :(
Unity is already giving headache

---

### Post by ZOMGxuan on 2012-09-28
For those of you who are still having problems, you're probably having the same problem as described in [this thread]("http://ubuntuforums.org/showthread.php?p=12267525"). In that thread, a link to a [bug report]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/858845") containing a workaround was mentioned, and I've tried it and it works for me.

Basically, for whatever plugins you're having problems with the settings not persisting across logins or reboots (for me it was the Wall plugin), edit the /apps/compiz-1/general/screen0/options/active_plugins key in gconf-editor, and move the problematic plugins to the bottom of the list, below 'unityshell' (so I moved 'wall' below 'unityshell'). If you're having problems with the Expo or Scale plugin, move 'expo' or 'scale' below 'unityshell'.

This makes it so that those plugins are loaded *after* Unityshell is loaded, which is probably what is causing the problems because when the Unityshell plugin loads, it rewrites some of the settings of previously loaded plugins.

---

