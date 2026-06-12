---
title: "Cant install on my Laptop"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by renzokuken on 2006-10-29
ok, i'm trying to install Edgy on my new laptop. thing is i'm having probalems, it doesnt get very far at all.

i get to the initial splash screen where the options are something like

1. start or install ubuntu
2. start in safe graphics mode
3. etc etc etc......you know the menu i mean.

well i tried all relevant options on two edgy CD's and two Dapper cds (which i definately know work, both Alternate CD and the Desktop one)

but no matter what i choose, the process just stops almost straight after i choose an option. i just get the _ thingy flashing in the top left.

well i then tried a Dapper Live CD i had lying around and got the follow messages which i think are responsible but i have no idea what they mean

```
checking if image is initramfs...it isn't (no cpio magic); looks like an initrd
ACPI: Looking for DSDT in initrd...not found!
not found!

```

and thats where it stops.

please help. pleeeease. i havent used windows for over a year now and i really dont wanna have to start again now

thanks

EDIT: i forgot to say my laptop is an Evesham A240, with a dual core AMD Turion X2 TL-50.
i keep seeing people mention passing the "noapic" option with these cpu's. could this help me and so what is it and how do i do it?

---

### Post by mgolden on 2006-10-29
> **renzokuken said:**
> ok, i'm trying to install Edgy on my new laptop. thing is i'm having probalems, it doesnt get very far at all.


Can you tell us what kind of machine it is, especially what graphics card you might have?

---

### Post by renzokuken on 2006-10-29
i just edited the message above just before i saw your post. its an nvidia card.

---

### Post by renzokuken on 2006-10-29
*bump*

---

### Post by /carlito on 2006-10-29
Try adding noacpi and noapic to your boot line.

---

### Post by renzokuken on 2006-10-29
and how do i do that? 

sorry, been using ubuntu for a couple of years now but never had to add anything to my boot line before

---

### Post by renzokuken on 2006-10-29
ok, i tried the 64-bit cd and the same thing. after i select the first option, it comes up with "booting kernel" and just hangs, as before.

how do i correctly add the noapci and noapic options to the boot on and Edgy install CD?

---

### Post by /carlito on 2006-10-29
Press F6 on the menu and add "noapic noacpi" to the end of the line.

---

### Post by renzokuken on 2006-10-29
ok, i tried it and it still just hangs on a blank black screen with the underscore flashing in the top left corner.

EDIT: i tried to just install the server and got the **"DSDT not found"** error again

anyone know what this is and what i can do about it??

---

