---
title: "GRUB error 22"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by MSdefecter on 2008-01-27
Hi everyone,
                    I recently installed Ubuntu 7.10 64 bit as a dual boot with Win XP. I had problems with it and somebody at work suggested that I try the 32 bit version as this wasn't so glitchey. I tried to install it and it wouldn't install so stupidly I un-installed the 64 bit Ubuntu partiton in an attempt to solve this. When I tried to boot the system back into windows it gave me the error message GRUB 22 error. I guess this is because I removed the Ubuntu loader (GRUB) and as this probably replaced NTLDR for windows I now cannot get into XP. Now just to add to my problem I tried to reinstall the 64 bit version so I atleast had something and it wouldn't go past the graphics mode select screen. Does anyone know what I can do to help me get back into my PC which as things currenty stand is just a very expensive paperweight!
                                        Thanks alot,
                                                          MS defecter

---

### Post by vojtech.t on 2008-01-27
You have to recover the WIndows Loader - boot Windows Install CD &#8594; go to Recovery Console and use command 'fixmbr'.

'http://pcsupport.about.com/od/termsf/p/fixmbr.htm
[http://pcsupport.about.com/od/termsr/p/recoveryconsole.htm](http://pcsupport.about.com/od/termsr/p/recoveryconsole.htm)

---

