---
title: "Thank god for XP!..."
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2006-06-04
Without XP, I wouldn't be able to reach these forums for help!!!
First admission...ubernoobie.
Updating Breezy to Dapper with 2 machines, both having xserver issues.  "x is not installed".  I've followed a link in upgrade section on xserver issues without success.  System= Dell P4, ~4yo, NVIDIA Geforce 4MX420.
I did the following:
dpkg-reconfigure xserver-xorg   and answered all the questions, mainly with defaults, then:
dpkg-reconfigure gdm
reboot
But still no joy--is this common?  Any solutions?  (comment: this sure ain't easy for a newb!  I'm pretty motivated to succeed but most recent switchers from XP would likely can this and return to the warmth of mother blue!)
Thanks for any advice.

---

### Post by Chickenmonger on 2006-06-04
Does the Dapper LiveCD come up with X working on either machine?

---

### Post by flyingsolo on 2006-06-04
I did upgrade via synaptic.  First updated system, then upgraded OS, so no live CD employed.  I [COLOR="Blue"]HAD[/COLOR] Breezy working just fine but now am without Ubuntu.](*,)

---

### Post by steveneddy on 2006-06-05
When you do this:

sudo dpkg-reconfigure xserver-xorg

don't list the PCI or AGP address on the video card. Blank out or erase the address that the reconfig program gives you. That works for me & I have Nvidia card, also.

I has issues when I upgraded & I had to relearn this step. It drove me mad for a few hours until I literally slept on it.

After you reconfig, don't forget to:

sudo /etc/init.d/gdm restart

Good luck.

-SE

---

### Post by steveneddy on 2006-06-05
[QUOTE=Chickenmonger]Does the Dapper LiveCD come up with X working on either machine?[/QUOTE]

I wonder if he installed the server version? There is no X in the server version of Dapper. You have to get the Desktop Ubuntu to get X.

-SE

---

### Post by flyingsolo on 2006-06-05
Sorry--I had to sleep on this so missed seeing posts above.
No, I don't think this is a server install since it was an upgrade via synaptic while in the Breezy desktop.

---

### Post by tseliot on 2006-06-05
[QUOTE=flyingsolo]Without XP, I wouldn't be able to reach these forums for help!!!
First admission...ubernoobie.
Updating Breezy to Dapper with 2 machines, both having xserver issues.  "x is not installed".  I've followed a link in upgrade section on xserver issues without success.  System= Dell P4, ~4yo, NVIDIA Geforce 4MX420.[/QUOTE]

1) Were you using the Nvidia driver before upgrading?
2) Did you set the driver to "nv" or "vesa" when you did a dpkg-reconfigure xserver-xorg ?

---

### Post by flyingsolo on 2006-06-05
Because I was very new at Linux when setting up this machine, I really don't recall if I had specific nvidia driver or used the "nv" selection (I think it was the latter)  But with my upgrade attempt, i've tried nv, vesa, vga--all without success.

---

### Post by tseliot on 2006-06-05
[QUOTE=flyingsolo]Because I was very new at Linux when setting up this machine, I really don't recall if I had specific nvidia driver or used the "nv" selection (I think it was the latter)  But with my upgrade attempt, i've tried nv, vesa, vga--all without success.[/QUOTE]
Try this command then (it won't ask you ant questions):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and then type:
```
reboot
```

---

