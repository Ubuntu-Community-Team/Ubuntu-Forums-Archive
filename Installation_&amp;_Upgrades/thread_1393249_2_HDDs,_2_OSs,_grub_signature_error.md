---
title: "2 HDDs, 2 OSs, grub signature error"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by Dayofswords on 2010-01-29
i've had xp on a hard drive for a while and also had a hard drive just doing nothing, si i put ubuntu on it and had it as the first booting disk with xp still hooked up, installed fine, everything works, but after running *update-grub2* to get the xp as an option, it outputted this
```
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
**grub-probe: error: Cannot find a GRUB drive for /dev/sdb1**.  Check your device.map.

done


```
with that error there i decided to see if it even worked with xp. restarted and choose xp, it gave me a signature error and press any key to continue.

can i fix this? so that i can boot into ubuntu or xp even though they are on different drives, currently i manually switch the cables to boot

---

### Post by byStanderone on 2010-01-29
...sudo update-grub

---

### Post by audiomick on 2010-01-29
> **byStanderone said:**
> ...sudo update-grub

to elaborate a bit,

you need to be booted into Ubuntu with both HDs plugged in.

Open a terminal
system> accessories> terminal

type in
```
sudo update-grub
```
an then you user password when asked for it. You wont see what you are typing.

That makes grub go off and have another look at what is there, and update it's config file.

---

### Post by darkod on 2010-01-29
Also if it keeps complaining about device.map I think you generate a new one with:

sudo grub-install --recheck

---

### Post by meierfra. on 2010-01-29
> Also if it keeps complaining about device.map I think you generate a new one with:

```
sudo grub-install --recheck
```

The command to generate the device.map is

```
sudo grub-mkdevicemap
```

---

### Post by darkod on 2010-01-29
> **meierfra. said:**
> The command the generate the device.map is

```
sudo grub-mkdevicemap
```

Sorry. :oops:

---

### Post by Dayofswords on 2010-01-30
> **byStanderone said:**
> ...sudo update-grub
> **audiomick said:**
> to elaborate a bit,

you need to be booted into Ubuntu with both HDs plugged in.

Open a terminal
system> accessories> terminal

type in
```
sudo update-grub
```
an then you user password when asked for it. You wont see what you are typing.

That makes grub go off and have another look at what is there, and update it's config file.
well, that is what i did, just didnt put sudo in the description(guess i should next time), thought it was implied for grub changes.
they are both plugged in, i just have to manually switch them to boot since i have yet to figure out how to get into bios to changed the boot order(its old, doesnt tell me how, eg. F5=setup, google didnt help so much so far)

off to go to try 'sudo grub-mkdevicemap', i did attach the xp drive after installing, so that could be why
**opens cover to swap**

---

### Post by munnster on 2010-04-14
> **meierfra. said:**
> The command to generate the device.map is

```
sudo grub-mkdevicemap
```

Thanks for this!  It worked perfectly! :P

---

