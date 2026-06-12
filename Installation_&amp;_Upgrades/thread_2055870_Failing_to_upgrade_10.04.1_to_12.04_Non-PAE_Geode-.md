---
title: "Failing to upgrade 10.04.1 to 12.04 Non-PAE Geode-GX2"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by hombibi on 2012-09-10
Hi,

On trying to upgrade a small ubuntu 10.04.1 server to 12.04 the upgrade stops with the message: 

> No i686 CPU 

Your system uses an i586 CPU or a CPU that does not have the 'cmov' 
extension. All packages were built with optimizations requiring i686 
as the minimal architecture. It is not possible to upgrade your 
system to a new Ubuntu release with this hardware. 

Restoring original system state

Aborting

```
uname -m
``` reports i586
and 
```
sudo lshw -class cpu
``` reports:
>   *-cpu                   
       description: CPU
       product: Geode(TM) Integrated Processor by National Semi
       vendor: Geode by NSC
       physical id: 4
       bus info: cpu@0
       version: Geode GX2
       serial: Processor Serial Number
       slot: BGU396
       size: 399MHz
       capacity: 399MHz
       width: 32 bits
       clock: 33MHz
       capabilities: fpu fpu_exception wp de pse tsc msr cx8 pge cmov mmx mmxext 3dnowext 3dnow up

Based on the decision of the Ubuntu Technology Board ([https://wiki.ubuntu.com/TechnicalBoard/TeamReports/11/December](https://wiki.ubuntu.com/TechnicalBoard/TeamReports/11/December)), that 12.04 continues (and is the last release) to support Non-PAE cpu's and the information above I expected to be able to upgrade once more. 

However the upgrade fails because of a check in a script DistUpgradeQuirks.py 

```
        # check family
        if re.search("^cpu family\s*:\s*[345]\s*", cpuinfo, re.MULTILINE):
            logging.debug("found cpu family [345], no i686+")
```

that is written to a /tmp subdir when the upgrade is started with "sudo do-release-upgrade". As result of the failing check the upgrade is subsequently aborted.

Does anyone know how I can continue the upgrade succesfully?

---

### Post by hombibi on 2012-09-21
Here is the answer:

[https://help.ubuntu.com/12.04/installation-guide/i386/hardware-supported.html#id2615549]("https://help.ubuntu.com/12.04/installation-guide/i386/hardware-supported.html#id2615549")

But I don't understand it: i586 platforms are still sold, search for Alix for instance. And AMD continues to produce and sell the GEODE LX platform (i586 introduced in 2007) until 2015.

I am not sure about the numbers of users of these systems, but it is a pity that I and the rest of these users are forced to find another distribution.

So, my question: does anyone know of a distribution that is actively going to be maintained for the i586 cpu family for the next years?

---

### Post by jerrrys on 2012-09-21
Found this, hope its still true :)

[http://answers.yahoo.com/question/index?qid=20090926094153AA3VsaG](http://answers.yahoo.com/question/index?qid=20090926094153AA3VsaG)

---

### Post by hombibi on 2012-09-23
Thanks Jerrys,

I followed your link and checked their site. Unfortunately the maintainers are not very clear. The site states that Puppy Linux will run on "old" hardware. No word on the future, or whether old includes i586. I guess I have to try and see. :P  Thanks for your help.

---

