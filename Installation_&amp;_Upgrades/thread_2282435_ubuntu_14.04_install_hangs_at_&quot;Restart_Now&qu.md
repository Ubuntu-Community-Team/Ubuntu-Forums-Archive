---
title: "ubuntu 14.04 install hangs at &quot;Restart Now&quot;"
date: 2015-06-14
forum: Installation &amp; Upgrades
---

### Post by Neys on 2015-06-14
Hi all,

I am having a bit of trouble with installing ubuntu 14.04. I had previously (successfully) installed Centos 7 and Ubuntu, but am trying to go back to Ubuntu on a bigger partition after a testing phase. System is a dual boot with Windows 7 64bit on an intel i-7.

I can use the Try Ubuntu option, so I believe the installation media is ok (USB), and the install proceeds as expected right up until the Restart Now screen. When I select restart now, the message disappears and I am left with the background but no further actions take place. The only way to exit the screen is Alt-PrntScrn R E I S U B, so I can get back to the grub. Ubuntu starts ok, but then is unable to shut down at any point.

I've tried starting over (deleting partitions, reinstalling), updating etc, but I am getting nowhere and the same error occurs.

Any help would be greatly appreciated!

Neys

---

### Post by grahammechanical on 2015-06-14
If you are going to install Ubuntu again, this time do not accept the offer to "restart now." Accept the offer to "continue testing" and shut down the live session from the power/cog menu. We should get a message to remove the disc/USB and press Enter.

If it is an installed Ubuntu that is not shutting down, then there are two commands to run. The first will restart. The second will halt. 

```
sudo shutdown -r now
```
```
sudo shutdown -h now
```

We can run those commands from the terminal or a Linux console. Ctrl+Alt+F2 as an example.

If there are any error messages then they would be useful things to add to your thread.

Regards.

---

