---
title: "Upgrade from 16.04 lts to 18.04 lts: boot stops before login screen"
date: 2018-10-18
forum: Installation &amp; Upgrades
---

### Post by pickelhaupt on 2018-10-18
I have a Samsung NP700G7C laptop with dual os (win7 + ubuntu LTS dist since 12.04). 

I upgraded from 16.04 LTS to 18.04 LTS two days ago after doing some clean up of old packagaes, etc. 

The problem is that it will not boot properly since the upgrade. I get past Grub allright, but after a while it gets stuck and I get a terminal screen with a heap of commands and messages.
On that screen there is a suspisious message reading:

"Gave up waiting for suspend/resume device /dev/sdc2: clean, 460444/4227072 files, 3873619/16878290 blocks".

After extensive searching I gather that there is probably some problem with encrypted swap partition and/or graphics drivers (nvidia).

I can access tty as root so if anyone has a proposed chain of commands (code) on how to proceed in isolating the problem and curing it I would be grateful. The kernel version is 4.15.0-36-generic

---

### Post by pickelhaupt on 2018-10-19
Progress of a kind:

Tried to switch from gdm3 to lightdm. This made it possible to login. However, the screen resolution was terrible low. After switching back to gdm3 it reverted to tty1 view and boot freeze.

---

### Post by dino99 on 2018-10-19
As you have made a dist-upgrade, think to clean the system to purge obsolete dependencies and settibgs.
Use gtkorphan & bleachbit (as root, carefully select settings).

Depending on the graphic driver used, gdm3 sometimes gives unexpected result like yours. Test without third party packages (if any) and glance at 'journalctl -b' to find useful warning (highlighted lines) / error (red lines)

---

### Post by pickelhaupt on 2018-10-20
Well, I updated graphics drivers with:
```
sudo ubuntu-drivers autoinstall
```

That fixed the super low resolution on login screen.

Now I got stuck in the infamous login loop.
I fixed that with this command in tty:
```
mv .Xauthority .Xauthority.bak
```

Now I can actually enter Ubuntu 18.04 LTS desktop and screen resolution is fine.

It is working using lightdm, but still not with gdm3. So I don't consider this issue solved. 

Any takes on the lightdm/gdm3?
It very much resemble the issue described here [https://askubuntu.com/questions/1050672/gdm3-does-not-start-in-ubuntu-18-04](https://askubuntu.com/questions/1050672/gdm3-does-not-start-in-ubuntu-18-04)

---

