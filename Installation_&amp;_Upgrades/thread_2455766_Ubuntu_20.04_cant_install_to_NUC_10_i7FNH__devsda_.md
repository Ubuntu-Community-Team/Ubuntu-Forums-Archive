---
title: "Ubuntu 20.04 cant install to NUC 10 i7FNH  dev/sda errors"
date: 2020-12-27
forum: Installation &amp; Upgrades
---

### Post by voxpopili on 2020-12-27
Just sharing a fix in case anyone else has problems installing Ubuntu on to a Intel NUC10 i7

I tried a clean install on to a new Intel NUC 10 th Gen i7 FNH with both 20.04 and 20.10

It kept crashing with error messages ;
 
error fsynching/closing/dev/sda:input/output error

input output error during read on /dev/sda

I used both Rufus and Yumi to create the ISO but the same issue came up.

The solution was a BIOS update using F7 , see text on link below.

You must first go into bios with F10 at startup then tick for F7 to be an active key during boot , the download for FN0047.cap is below , paste it onto a thumb drive and reboot , hit  F7 , give it time to flash and dont interrupt it if the screen goes black for a while.

[https://www.intel.com/content/www/us/en/support/articles/000033291/intel-nuc.html](https://www.intel.com/content/www/us/en/support/articles/000033291/intel-nuc.html)

There are several options of downloads , some are labelled Ubuntu specific and some are labelled "OS independant"

[https://downloadmirror.intel.com/30073/eng/NUC-AptioV-BIOS-Update-Readme.pdf](https://downloadmirror.intel.com/30073/eng/NUC-AptioV-BIOS-Update-Readme.pdf)

It worked for me , my system is flying like a dream

---

### Post by tea for one on 2020-12-27
> **voxpopili said:**
> some are labelled "OS independant"

It worked for me , my system is flying like a dream

Splendid - it's good to read successful solutions.

I have an older NUC8 and I have always been very happy that you can update the UEFI independently via a USB stick.

It is a pity that all PC suppliers/manufacturers do not follow this OS agnostic method.

A minor irritation is that Intel still insist on the term [COLOR="#FF0000"]Visual BIOS[/COLOR] or, in your case, [COLOR="#FF0000"]Aptio V BIOS[/COLOR], when it is [COLOR="#0000FF"]UEFI[/COLOR].

---

