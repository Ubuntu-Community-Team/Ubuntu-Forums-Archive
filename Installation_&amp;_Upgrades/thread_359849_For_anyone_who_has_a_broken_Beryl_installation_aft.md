---
title: "For anyone who has a broken Beryl installation after a kernel update (fglrx users)"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by dkbg on 2007-02-12
If you're using an ATI video card with the fglrx drivers and you used the guide at [wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") (or any guide really), you need to remember to **recompile the fglrx kernel module** after a kernel update (look at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Install_the_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Install_the_Driver_Manually")).

> Compile the kernel module:

```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```

**IMPORTANT: You have to recompile the kernel module after each kernel update!** 

I forgot to do this after I received some kernel updates. My Beryl installation was dead (it wouldn't start on startup and selecting it in the beryl-manager task tray icon would just cause the window title and borders to flash off, then on again, because it was just reverting back to Metacity), I was getting very high Xorg CPU usage, and everything was extremely choppy with some strange diagonal jagged window redraws happening.

I was panicking for a while, trying to remember what I had done recently, then I realized what had happened after browsing that wiki again. After following only the recompile instructions (the ones given aboce, sudo module-assisant...etc.) everything worked perfectly again after a restart.

Please, don't forget this, and don't go through the same fright I had! :)

(If this post is in the wrong forum, sorry admins, you can move it of course. I wasn't sure where to put it, the general discussion area didn't seem suitable since this would be of most help to people looking for support, and in the cafe it wouldn't get that exposure.)

EDIT: Damnit, I just realized I put this in a terrible place, it should be in the Video support forum... Please move it wherever... Sorry about this.

---

