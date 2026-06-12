---
title: "ati graphic driver"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nyinyizaw on 2010-03-27
I can't activate ati/amd mobility redeaon 4330 in propriety driver . so,Ican't activate any effect . Please help me  ? ubuntu 10.04 LTS

---

### Post by QIII on 2010-03-27
There are some unfortunate problems with the AMD/ATI drivers going on at the moment.  AMD/ATI has, for the past few Ubuntu versions, made sure that their latest driver is available in the Ubuntu repos in time for the official release.  Everyone else has to wait. This is the case again for Lucid.

Also unfortunately, the current driver available outside the Ubuntu repos does not seem to play well with the version of Xserver in Lucid.

Remember that Lucid is a beta and the AMD/ATI driver included in the repos is a pre-release.  The kinks aren't entirely worked out.  I have a bug report on Launchpad.

That said...

If you are not comfortable with the CLI, use Synaptic to remove fglrx and fglrx-amdcccle.  Don't just deactive the driver.  Uninstall it.

Or, from the CLI

```
sudo apt-get remove fglrx fglrx-amdcccle
```

That will cause the use of the open source driver by default.  The open source driver supports Compiz and effects.  However, it does not support multiple X sessions for multiple monitors, so you will have to put up with a single desktop across all of your monitors if you have more than one.

---

### Post by Mark Phelps on 2010-03-27
Lucid is still in beta testing.  If you're not a seasoned, experienced Ubuntu user, you should not be using a beta version of the OS.

If you want to use it, then post your questions in the correct beta testing forum -- Development & Programming, Lucid Lynx Testing.

I'm requesting the Mods move this thread to that forum.  Look for any further response there.

---

### Post by Perfect Storm on 2010-03-27
Thread moved to Lucid Lynx Testing and Discussion.


nyinyizaw, I'll recommend you also read the stickies in Lucid Lynx Testing and Discussion.


Happy testing ^_^

---

### Post by rajeev1204 on 2010-03-27
> **nyinyizaw said:**
> I can't activate ati/amd mobility redeaon 4330 in propriety driver . so,Ican't activate any effect . Please help me  ? ubuntu 10.04 LTS


Insall the fglrx package from synaptic, then from terminal type:

[```
sudo aticonfig --intial
```

reboot.

---

