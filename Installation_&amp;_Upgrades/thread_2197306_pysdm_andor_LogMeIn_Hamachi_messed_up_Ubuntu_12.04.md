---
title: "pysdm and/or LogMeIn Hamachi messed up Ubuntu 12.04 LTS/Linux Mint Cinnamon dual-boot"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by ajkariapper on 2014-01-03
Hi there,

I'm a newbie in the Ubuntu world and have ended up messing up my first Ubuntu installation.

Setup:
32 bit Toshiba Satellite Pro L300
Dual-boot with Ubuntu 12.04 LTS and Linux Mint Cinnamon

Everything was running fine (the system had been in regular use for two weeks) until I tried to use the pysdm tool to automate mounting of the Linux partition from within Ubuntu. Since then, the system refuses to go beyond the Ubuntu logo screen with the five orange dots. I can access the Ubuntu partition from within Mint and used that to try to fix issues that I may have caused due to a poor understanding of pysdm. That didn't work too well, so I tried using the Boot-Repair tool on my live Ubuntu USB to fix the boot configuration. I got a success message at the end but the system still does not boot:
a. from recovery mode, if I choose the failsafe GUI option, I get to the Ubuntu logo screen with the five orange dots. I'm able to use Ctrl+Alt+F2 to get to a terminal from where I can shut down the system.
b. if I go with regular Ubuntu, I get a black screen and no disk activity and no response to any typed commands, not even Alt+SysReq+R E I S U B. Have to use the power button to power off.

The results of boot-repair's analysis are here: [http://paste.ubuntu.com/6683501/](http://paste.ubuntu.com/6683501/)

I hope you can help me. Really lost after 6 hours of trying to recover from this issue.

Thanks in advance!

---

### Post by ajkariapper on 2014-01-03
In case this is useful for the diagnosis:

From the recovery mode panel, if I choose the option to resume booting, I get some output before the screen goes black. One of the issues seems to be an error about being unable to connect to the system bus, followed by a long path to a file that it can't find.

Similarly, when I choose the option to enable networking from the recovery menu, I get an error from the Modem-Manager about not being able to connect to the system bus.

I'm now wondering if these problems are due, not to pysdm, but to the LogMeIn Hamachi Engine I installed in the same session. I had not noticed the installation instructions about first installing LSB (3.0 or above), so could the problem I'm experiencing be due to that?

---

