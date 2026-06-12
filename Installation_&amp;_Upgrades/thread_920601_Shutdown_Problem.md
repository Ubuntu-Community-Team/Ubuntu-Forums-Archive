---
title: "Shutdown Problem"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by jessel on 2008-09-15
I have installed Ubuntu 8.04.

Everything seems to work pretty good, but I am unable to use the "shutdown" button. I don't know if there is a way that I can modify my sytem or if I am having a hardware issue for which there is no solution at the present time.

I have tried several different booting parameters in grub:
1) force acpi  ("acpi=force")
2) enable apm and disable acpi  ("noacpi acpi=off apm=on noapic" & add "apm" line to /etc/modules)
3) disable both acpi and apm

I have also tried to shutdown at the command line (su implied):
1) shutdown -h now
2) shutdown -P now
3) poweroff -f ( this made everything freeze up!!)

Anyhow the typical behavior is to stay on showing the splash shutdown screen...

My computer:
motherboard: dg965ry
processor: dual core (i don't remember the exact name)

Thanks

---

### Post by Partyboi2 on 2008-09-15
I have had similar problem with a few machines in the past and found that my problem was to do with the power settings in the bios.

---

### Post by jessel on 2008-09-25
> **Partyboi2 said:**
> I have had similar problem with a few machines in the past and found that my problem was to do with the power settings in the bios.

Thanks for the reply.

I had tried changing the BIOS settings, but nothing worked for me.

The only thing I found is that you can use grub to shut the computer down. So, now I restart from Ubuntu then I select an option from the grub menu (that I added) which runs the "halt" command.

The fact that grub can shut the computer off makes me think I should be able to get ubuntu to do it. Yes, I realize that grub is a totally different system that independantly controls the computer. But, now that I have a way to shut the computer down (nicely) I have not really spent much time looking at it.

---

### Post by wpshooter on 2008-09-25
Have you tried from the terminal:  sudo shutdown now -h

---

### Post by jessel on 2008-09-25
Thanks for the reply.

I've always used "shutdown -h now". I don't suspect using "shutdown now -h" would act much differently, but I will  give it a shot. However, I'm at work now...

---

### Post by nibbslang on 2008-10-20
Yea!!  I got a phone call from Dell today to tell me that my mini 9 will be delivered on Wednesday :)  thats two days early. :)

Well actually!!  I'd better not get too excited as it is Dell afterall, guess I will believe it when I see it

---

### Post by jessecollins on 2008-11-04
> **jessel said:**
> Thanks for the reply.

I've always used "shutdown -h now". I don't suspect using "shutdown now -h" would act much differently, but I will  give it a shot. However, I'm at work now...

Any updates on this?  I'm having the same issue.  Thanks in advance.

---

### Post by erace on 2009-01-05
I've had the same problem. Does anyone know? Some years ago the problem wasn't there. Everything worked fine, say 5 years ago. Then I installed a new version of ubuntu 2 years ago and since then I haven't been able to shut it down properly. 
I've tried various acpi flags to kernel at boot. If I don't the kernel screams "acpi: unable to initiate acpi"or something like that. From what I've read it has something to do with the via-chipset I use (an old MSI KT-266 motherboard). It has ACPI functionality according to MSI. I don't know how to get this working. Is there anyone who knows? Somewhere I read that it had something to do with how the disks are shut off and I tried alter some shutdown scripts but it didn't really do the job as I had wanted it to.

---

### Post by jessel on 2009-03-19
this problem went away, seemlessly after I upgraded the kernel. I have been careful after I install a new kernel, I find some will not operate my sound card.

I think that it is/was just a matter of campatibility, perhaps if someone is having this problem, they just want to install some different kernels and its pretty easy to try them out since grub gives you a menu when you boot up.

---

### Post by veredoron on 2009-03-19
i think i am experiencing same problem - since i updated a newly installed 8.1 ubuntu - i cannot shut it down from the "start" button (on the right top of the screen) - prior to the update i had few options on this button like restart and shut down - now i have only guest session/lock screen/log out - so i cannot shut it down from there - how do i get my button back ???

---

### Post by jessel on 2009-03-20
Maybe if you remove the widget then add it again you'll be presented with an option to shut down.

Right click on the switch users widget and you can add users, so this probably doesn't help.


Right click on the panel and select "add to panel" select "shutdown"...

---

### Post by jessel on 2010-02-17
just for the record I did discover what the problem was:

when I enabled the onboad LAN on my motherboard the system would not shut down properly (it just froze up). This was only applicable when I was running hardy. what I did was install jaunty on a free partition and test it out. i could reproduce the problem, and it was definitely caused by enabling the onboard lan, and for whatever reason running jaunty i do not have this problem. so I run jaunty and everything is good!

my motherboard is the intel dg965ry

---

