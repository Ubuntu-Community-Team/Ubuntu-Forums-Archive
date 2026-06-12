---
title: "upgrade problem"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by Skeemom on 2012-05-09
I received a message that Ubuntu 12.04 is available for installation.  I opted to upgrade to it.  All went well up to the final operation.  The progress report was reading  "Cleaning up" when the power went off.  After a couple of minutes the power came back on and I booted up.  Of course the installation program was gone.
"About Ubuntu" on my help screen says 12.04 is installed.  Everything seems to be running OK.  

I'm just wondering what went undone and do I need to do anything to finish the clean up?  Whatever that is.

Thanks,

Sam Keenon

---

### Post by wilee-nilee on 2012-05-09
If your up and running you are probably okay, you can run these two commands to clean out extras uneeded config packages. You will probably be asked for a yes or no on either command just say yes=y and copy and paste the whole command.

```
sudo apt-get autoremove && sudo apt-get autoclean
```

---

### Post by Skeemom on 2012-05-10
Thanks.  That was just what I was looking for.
Sam

---

### Post by wilee-nilee on 2012-05-10
> **Skeemom said:**
> Thanks.  That was just what I was looking for.
Sam

Cool, enjoy this release. :D

---

### Post by mörgæs on 2012-05-10
Please mark the thread 'solved'.

---

