---
title: "Ubuntu 18 not booting after apt-get update &amp;&amp; apt-get upgrade"
date: 2021-01-11
forum: Installation &amp; Upgrades
---

### Post by dniven on 2021-01-11
[SIZE=3][FONT=arial]Hi Folks,

Ran Boot-Repair with the following report:

[/FONT][/SIZE][COLOR=#000000][FONT=Menlo][SIZE=3][FONT=arial]http://paste.ubuntu.com/p/wWqGswQ589/

Any suggestions or recommendations most appreciated!

Thanks!

[/FONT][/SIZE]
[/FONT][/COLOR]

---

### Post by CelticWarrior on 2021-01-11
Line 105: *[COLOR=#000000]Please [/COLOR][COLOR=#AA22FF]**do**[/COLOR][COLOR=#000000] not forget to make your UEFI firmware boot on the Ubuntu [/COLOR][COLOR=#666666]18[/COLOR][COLOR=#000000].04.5 LTS entry [/COLOR][COLOR=#666666]([/COLOR][COLOR=#000000]nvme1n1p1/EFI/ubuntu/grubx64.efi file[/COLOR][COLOR=#666666])[/COLOR][COLOR=#000000] ![/COLOR]*

---

### Post by dniven on 2021-01-11
Does that mean simply choosing that from the BIOS settings or something else? I'm not entirely clear on what it's asking me to do. Thanks to clarify!

---

### Post by CelticWarrior on 2021-01-11
By now, you should have the matters about UEFI (which is NOT BIOS, it replaces BIOS) a lot more clear, considering your other thread.
Differences between BIOS/Legacy installations and the proper UEFI mode, as well as the different OSes requirements for one and the other, including but not limited to partitioning type (MBR vs GPT), is on a MUST know basis for anyone installing OSes and even more so when dual- or multi-booting.

Yes, it's in the UEFI settings (still called "BIOS settings" wrongly) > Boot menu.

---

### Post by dniven on 2021-01-11
Thanks for your patience and for clarifying to use UEFI and not BIOS. This is new terrain for me so I apologize for the newbie questions.

Below are the UEFI choices: the last three (ubuntu, UEFI OS, ubuntu) all lead to a grub menu.

Ideas on what to do next?

[FONT=&amp]https://imgur.com/IiMTYHn

[/FONT][IMG]https://imgur.com/IiMTYHn[/IMG]

---

### Post by CelticWarrior on 2021-01-11
Only one should work; the other is a leftover from a previous installation (probably).

Isn't a Grub menu what you want? Or doesn't Ubuntu boot normally after that?

---

### Post by dniven on 2021-01-11
I'd like it to boot right into Ubuntu! Am happy to send you some beers if I can get this thing to boot!

---

### Post by CelticWarrior on 2021-01-11
OK, let's first try
```
sudo update-grub
```
Reboot.

If no change then the problem stems from that leftover "Ubuntu" and a very delicate operation has to be done with 'efibootmgr' to remove the non-working Ubuntu entry.

Obtain the list and order of the boot entries running ```
efibootmgr -v
```
Take note of "BootOrder". The first number corresponds to your current (working) Ubuntu installation, the other "Ubuntu" is the one to remove:
```
sudo efibootmgr -Bb <number>
``` where number is the 4 digits number of the entry to remove.

Needless to say one mistake here and you may not boot at all.

---

### Post by dniven on 2021-01-11
Just to be clear, I should run [COLOR=#000000][FONT=&quot]sudo update-grub[/FONT][/COLOR] from the Live USB disk, right? Not from the Grub menu right?

---

### Post by CelticWarrior on 2021-01-11
The first command - 'sudo update-grub' - is to be run from the running Ubuntu (as all commands suggested here unless otherwise specified).

---

### Post by grahammechanical on 2021-01-12
Did you notice this?

> Additional repair will be performed: unhide-bootmenu-10s 

If Ubuntu is loading but you are seeing the Grub menu and you do not need or want to see the Grub menu because Ubuntu is the only OS then you need to change that setting.

We do that by editing a file at /etc/default/grub and then running

```
sudo update-grub
```

That command runs a script that runs something called grub-mkconfig which in turn generates the grub.cfg file which we do not edit directly. A quote from /etc/default/grub

> # If you change this file, run 'update-grub' afterwards to update /boot/grub/grub.cfg.

From the official Grub manual

> ‘GRUB_TIMEOUT’
Boot the default entry this many seconds after the menu is displayed, unless a key is pressed. The default is ‘5’. Set to ‘0’ to boot immediately without displaying the menu, or to ‘-1’ to wait indefinitely.

Regards

---

### Post by dniven on 2021-01-13
Well, I learned that many of the key directories such as /usr and /sys also went poof after the apt-get upgrade and reboot, so I had to reinstall Ubuntu from scratch. No wonder it couldn't boot. Thanks for your pointers though, it was a great learning experience going through these steps.

---

