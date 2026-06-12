---
title: "Upgrade hardware"
date: 2017-11-09
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2017-11-09
Hi.
If I change all hardware except the harddisk, are there something I can do after, so it's go quicker? Some reconfiguring or something.

I have found that if I change the grafic card (gfx), it's better if i change to open drivers in stead of using propretarian drivers before I change the card.

/ Cheers Azyx

---

### Post by RobGoss on 2017-11-10
Changing your hardware is always a good thing,  is there any  particular reason why you would like to change your hardware

The reason I ask is Ubuntu runs very well on most machines including older ones. I would suggest to try what ever flavor of Ubuntu first and see how it runs before you start spending any money, unless it's something you really have your heart set on

---

### Post by DuckHook on 2017-11-10
> **Azyx said:**
> Hi.
If I change all hardware except the harddisk, are there something I can do after, so it's go quicker? Some reconfiguring or something.

I have found that if I change the grafic card (gfx), it's better if i change to open drivers in stead of using propretarian drivers before I change the card.

/ Cheers Azyx
Based on your sig, you are running some versions that are past end-of-life. In the case of Lubuntu-Trusty, it is now dead. Therefore, you may wish to install pristine versions of something like Lubuntu-Xenial which is good until 2019. You can decide whether you wish to upgrade to Beaver when the time comes.

If doing a pristine install anyways on new equipment, then there isn't anything to reconfigure. It's a pristine install. You will want to backup your old HDD and copy the data back into your new install.

However, Ubuntu-Trusty proper is still being maintained. If you wish to simply switch your old HDD into new HW, then you've already noted the single biggest preparation step: revert to default open-source video drivers. You might also wish to disable any added PPAs, disable any custom kernel parameters, back out HW-specific drivers and firmware extensions, etc. It's hard to advise you on such an open-ended question. We have no idea what you've customized or changed.

My best advice is more general: a complete HW overhaul of the sort you are thinking about is an ideal time to install a pristine system instead of just transferring the HDD and living with the old one. Unless you have reasons for doing so that you haven't told us, the new computer is an opportunity to start fresh without inheriting the cruft and inefficiencies that have accumulated over the years. It's true that you must backup and restore your personal data, but a backup should be done in preparation for such major surgery in any case.

If you choose this route, then make a detailed list of your settings, preferences and customizations before making the move. If the only component that you intend to keep is the HDD, then also consider going all the say and investing in a SSD. That way, none of your old HW is needed and you can convert your old box into a server of some kind. It also gives you a machine to fall back on and allows you to slowly move over your data at your leisure, which is a luxury that you will appreciate if you run into an installation problem.

---

### Post by Azyx on 2017-11-10
I find better hardware in a recycling room and I don't want/have time to make a new install and install and configure all application. An easy way is just to install the old harddisk in a new computer. Even if Ubuntu run well on old hardware, so doesn't old hardware manage, for instance decode x265 decoded movies and run other tasks very slow. Is just the boot that seems slow and I wonder if there  are some way to reconfiguring the system so it boot faster? Maybe the boot-loader or something?

---

### Post by Azyx on 2017-11-10
DuckHook. Oh.. I only have 16:04 LTS on my computers nowdays or don't use them any more, will change the signature/footnote :)

I will read your full answer to morrow. Thanks :)

---

### Post by DuckHook on 2017-11-10
> **Azyx said:**
> DuckHook. Oh.. I only have 16:04 LTS on my computers nowdays or don't use them any more...
In that case, it makes sense to just bring the HDD over.
> **Azyx said:**
> ...Is just the boot that seems slow and I wonder if there  are some way to reconfiguring the system so it boot faster? Maybe the boot-loader or something?
In your case, because you are actually replacing with recycled HW that is still old, one of the lighter flavours is a good choice. Since you are already familiar with Lubuntu, there is no reason to change.

Re: slow booting: please ask that question by starting a new thread in the General Help subforum and post in that thread the results of:```
systemd-analyze blame
```...and:```
dmesg
```

---

### Post by Azyx on 2017-11-11
[**[COLOR=#C61919][B]DuckHook**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1256508") .

I don't have systemd on the system, yet :) Your command did not work. I probably upgraded the system from 14:04 LTS ?

Do you know if it only to select systemd in synaptic? But I do have systemd-service...

Yes. I had an AMD 64 3GHz X2, or something and the 'new' computer in the recykling room have a Intel  i5 4x3,5 GHz and DDR3 RAM :) The computer didn't start because a broken RAM, I find out :)

Cheers

/Edit. It was only 14:04 LTS on that HHD.I now remember that I tested to upgrade for a 1-2 years ago, but there was much that did not pass the test.

---

### Post by DuckHook on 2017-11-12
Since you are actually on Trusty (14.04), we are back to my first set of advice, which is to install a pristine Xenial (16.04).

Re: the problems that you ran into before.

Since you will be using different HW this time, it is unlikely that you will run into the same issues. However, it is because of the value of a fallback machine that my advice would still be to install into a different HDD. 

In the absence of systemd report, dmesg will still give you info about what takes a long time to load at boot. You can also hit <ESC> or <SHIFT> (can't remember which) during the boot process to suppress the splash screen and see all processes as they load. You should be able to see what process takes so long.

---

### Post by Azyx on 2017-11-12
Thanx. Will try to se why the marker on the plack screen blinking in 20 sec. It there it takes time.

Press shift during boot and come to GRUB. It says: 

error: attempt to read or write outside of 'hd0' . Enter rescue mode ..
grub rescue>

So it seems to be a problem with bootloadern, that the system takes time to solve. I will search to fix the problem.  Thanks :)

---

### Post by Azyx on 2017-11-12
When I press shift, I came to grub rescue> and I can not leave it now cos after reboot I allways come there :(
I have tried to follow a manual from ask ubuntu there the error messagde I had appeared. The attachmed picture , show how I tried, but it does not help :([ATTACH=CONFIG]277495[/ATTACH]

I tried diffent msdos-partitios, becourse i did not know there /root where. 

There was a lot of command that did not work in grub rescue>

PS. I have now fixed a startup-disk 14:04 and will see if I'm abel to boot into that.... The 'old' statupdisk did not boot, even then I selected it i BIOS.

---

### Post by DuckHook on 2017-11-12
It appears to me that your system is getting less and less stable. Pressing <SHIFT> should not bring you to grub-rescue. It may bring up the grub menu, but that's a completely different thing and a feature that is expected. BTW, it should have been the <ESC> key during boot-up that gets rid of the splash screen.

Do you have anything important on this HDD that is not backed up? Your equipment sounds like it may be rather old. I recommend that you backup your important data. If you can get a LiveUSB session running, then copy your important data to a USB stick or another drive. I would recommend a complete format of the HDD before installing a pristine Lubuntu-Xenial. You can then copy back your important data.

Whether you switch to another computer or continue operating on this one, you need to seriously question why things are suddenly going wrong. As I mentioned, simply pressing <SHIFT> during boot-up should not corrupt your HDD. Something was already wrong either with the OS or the physical HW beforehand.

---

