---
title: "New User: How to Install Printer"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Sethalos on 2007-05-20
Hello,

I'm a new user (Ubuntu Feisty). I'm trying to figure out how to install.

HP PSC 1410

I've never installed a printer, so I went to System -> Administration -> Printer

But it doesn't seem to find it in the Printer box.

Could someone provide me with some information or steps on what I need to do.  Parallel port connection. (LPT1) I believe is the setting I would use.

Thanks, 

Seth.

---

### Post by mitch.c on 2007-05-23
> **Sethalos said:**
> Hello,

I'm a new user (Ubuntu Feisty). I'm trying to figure out how to install.

HP PSC 1410

I've never installed a printer, so I went to System -> Administration -> Printer

But it doesn't seem to find it in the Printer box.

I'm going to assume cups is installed...

I think you need to use the hpijs ppd for this printer. If it's installed, you should be able to select it as HP PSC 1400 during the New Printer wizard.

If not, you need to install the hpijs-ppds package. Find it in Synaptic or:
```
$ sudo apt-get install hpijs-ppds
```
Then try to run New Printer again.

> **Sethalos said:**
> Parallel port connection. (LPT1) I believe is the setting I would use.
I took a quick look at HP's site and it looks like this is a USB printer, not LPT which means it should be auto-detected. Whats the output when your run:
```
$ lpinfo -v
```

---

