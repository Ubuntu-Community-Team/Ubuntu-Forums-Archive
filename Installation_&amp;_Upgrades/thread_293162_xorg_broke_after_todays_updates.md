---
title: "xorg broke after todays updates"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by dhawk312 on 2006-11-04
Today I updated Ubuntu but my xorg broke after I restarted.  It removed nvidia-glx during the update.  I tried removing and installing server-xorg and the generic and 386 kernels and restricted kernels.  I also ran dpkg-reconfigure xserver-xorg but nothing still.  I tried reinstalling nvidia-glx but that said I was missing dependencies which wouldn't install.  Can someone please help me?  
The sad part about this is that I was using my laptop as a demo to show off linux's capabilities on my college campus when this happened like 2 hours ago.

---

### Post by taurus on 2006-11-04
Are you using Dapper or Edgy?  And what is the error message when X fails?  What are the names of the dependencies?

---

### Post by dhawk312 on 2006-11-04
I am using Edgy, the message is just the blue screen that says xorg failed to start, the name of the dependency is nvidia-kernel

---

### Post by meep! on 2006-11-04
same thing happened to me :(
changing the driver from nvidia to nv in xorg at least gives you X.

I was using the nvidia beta driver, but that doesn't work even if I try to reinstall it, nor does the non beta driver. Quite irksome really.

---

### Post by dhawk312 on 2006-11-05
I did change the driver from nvidia to nv when I did dpkg-reconfigure xserver-xorg but that did nothing for me.  I am thinking about just forgetting about edgy and "downgrading" back to dapper.  At least in dapper my atheros wireless card worked and I don't have to worry about updates that kill my xorg as often.  Does anyone know how to fix this?  I have reverted to running XP until i can get this fixed for now.

---

### Post by taurus on 2006-11-05
Hey, if Dapper is running great on your machine, why even bother to upgrade or install Edgy since Dapper is LTS while Edgy is an bleeding edge release...

---

### Post by towsonu2003 on 2006-11-05
perhaps [https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/70195](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/70195) is a little related to your issues?

---

### Post by matsujin on 2006-11-05
Same thing here.. I tried also fresh install of Edgy and sudo apt-get install nvidia-glx gives me this:

The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.9625
E: Broken packages

So the problem is within the repo's.. I guess it will be fixed soon.. :cool:

---

### Post by Wijsneus on 2006-11-05
I have the same problem - my xorg complains about an API mismatch: Nvidea kernel module has version 1.08762 while xorg has 1.08776.

How do i fix this so i can use my machine tonight?

---

### Post by Wijsneus on 2006-11-05
nvm - a reboot fixed my problems. 

This is what happened: I updated my machine. Nexuiz wouldnt run, so i tried to restart x, which was now version 1.0-8776. The kernel however, was still running the old 1.0-8762 NVidea driver. ](*,) 

Maybe update manager should have told me to reboot my machine? i dont know, normally x wouldn't be restarted until the machine was rebooted.

---

### Post by useResa on 2006-11-05
I had the same problem, but have things working again.
Maybe what I did can help you also.
You can find what I did in this [post]("http://www.ubuntuforums.org/showpost.php?p=1718300&postcount=13").

---

### Post by towsonu2003 on 2006-11-05
I think you should report these problems as bugs to launchpad.net (unless already reported)

---

### Post by spider-man on 2006-11-05
> **Wijsneus said:**
> I have the same problem - my xorg complains about an API mismatch: Nvidea kernel module has version 1.08762 while xorg has 1.08776.

How do i fix this so i can use my machine tonight?

I fixed the problem by downgrading nvidia-glx. I did this by running
```
sudo apt-get install nvidia-glx=1.0.8762+2.6.15.11-1
```

You can check what versions of nvidia-glx are available with the following command
```
aptitude -v show nvidia-glx | less
```

Hope this helps

---

### Post by Tim.thelion on 2006-11-05
I had the same problem, I solved it by installing an running an application called envy. I document in this post my migration to edgy... [http://ubuntuforums.org/showthread.php?t=293681](http://ubuntuforums.org/showthread.php?t=293681)

---

### Post by meep! on 2006-11-05
> **useResa said:**
> I had the same problem, but have things working again.
Maybe what I did can help you also.
You can find what I did in this [post]("http://www.ubuntuforums.org/showpost.php?p=1718300&postcount=13").

Thanks, that worked great :)

---

### Post by dhawk312 on 2006-11-05
thanks for all the help. I just switched back dapper.  My new laptop should be in on Friday so I'll switch back to edgy with the new hardware.  I just have too much going on to worry about fixing stuff like this at the moment and I need a stable pc.

---

