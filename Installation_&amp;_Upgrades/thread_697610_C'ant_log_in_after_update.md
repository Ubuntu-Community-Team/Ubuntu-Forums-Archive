---
title: "C'ant log in after update?"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by blkmax on 2008-02-15
I am running Kubuntu and was wondering if you Ubuntu users were having trouble loging in after the latest updates. We are having issues with Kubuntu after the latest updates wich will not let us login to KDE. Since you use Genome I was wondering if you were having this issue as well. 

Just trying to sort out if its a Xserver problem od KDE problem.


many thanks

Marc

---

### Post by taurus on 2008-02-15
It drops you right back out to the GUI login screen after you enter your username and password?  Press <Ctrl><Alt>F2 to get to another console and see if you can log in from there.  Then, check to make sure you haven't filled up your harddrive to the capacity.

```
df -h
```

---

### Post by blkmax on 2008-02-15
Thanks, I can login using the console. I have 38gigs free of disk space. Many Kubuntu and debian users semm to be affected. It attemps to log in, but just comes back to the login prompt. I ran inotifywatch to monitor all Xsession.d and seems to be running fine with the last script running as 99X11-common_start. So this confuses me. I was wondering if poeple running Genome are not seeing this error, then it must be a problem with KDE/KDM. If they are, then it might be Xserver itself.


thanks

Marc

---

### Post by Helladog on 2008-02-15
It's likely the language update which caused the same problem for some...it can be fixed by removing the new and reinstalling the old...funny thing is, their still providing the same update.

If it is the language pack update causing the problem, this will fix it...

> sudo apt-get install language-pack-kde-en=1:7.10+20071120 language-pack-kde-en-base=1:7.10+20071012

---

### Post by blkmax on 2008-02-16
Thanks, I will try this on monday. Its a pain if the update is always there. It will break everytime we update. I was hoping to not have to Micro manage updates so much. I guess it will only be till the next language update and all will be rosy after that.

I hope.

Thanks

Marc

---

### Post by bretto_40 on 2008-02-16
Helladog,

I am running Gnome and I have just done some updates and I appear to be having this exact same issue.

I would love to try your suggested solution to this issue but as I am running Gnome I assume your command would not work with me.

I would replace all instances of KDE with Gnome and try it but I'm sure that's not the way to do it and I don't want to try incase it screws me up further.

Are you able to please provide the same solution tailored to Gnome?

Thanks if you can.

---

### Post by bretto_40 on 2008-02-17
OK, further development,

In the end I decided to do the above fix anyway and replace all instances of KDE with gnome.

This actually worked in the sense that it went through the motions, but it told me that I already have the latest version of that language pack and nothing was installed or updated. So nothing was changed.

I always boot up in the generic version of the Kernel rather than the 386 version because I have a quad core processor so I booted up in the 386 version which at least put me through to the desktop in low graphics mode because I don't have the drivers working properly in that version of the Kernel because I don't use it normally.

There I was able to bring up the update install history in Synaptic which lists all updates that I downloaded to somehow screw my install. The Language pack is NOT in this list.

Any other ideas?

Now that I have the list, is there a way to un-install the updates and return my system to the state it was in before I ran the updates? Then I could just intall each one one by one until I find the offender...

Sorry to bump this thread.

---

### Post by bretto_40 on 2008-02-17
OK,

Sorry for bumping but my issues have now been resolved and I will list my steps here for others who have the same issue and stumble across it.

I fixed the issue by following this thread:
[http://ubuntuforums.org/showthread.php?p=4161267&posted=1#post4161267](http://ubuntuforums.org/showthread.php?p=4161267&posted=1#post4161267)

I managed to find this one while looking further (I DID look before). Specifically what fixed my issue was re-installing my video drivers.

I run a NVIDIA Geforce 8500GT and it appears that the latest Xorg-core updates can screw the install by removing a symbolic link that is needed.

I followed the usual method of re-installing the driver and during the process it mentioned the following, which it usually doesn't:

File '/usr/lib/xorg/modules/extensions/libglx.so' is not a symbolic link.

So I think this is where the driver re-install fixed it.

I now have full desktop functionality restored as well as Compiz-Fusion.

I hope this helps someone who stumbles across this thread with the same issue and I apologise again for bumping this thread.

Cheers :)

p.s. there was mention that this may need to be done again once the xorg-core update is fixed; so hoping a re-install of the diver will fix again if this happens.

---

### Post by blkmax on 2008-02-18
Thanks HellaDog the language pack from above solved my login issue.

I must make sure not to upgrade this package in the near future. 


Marc

---

