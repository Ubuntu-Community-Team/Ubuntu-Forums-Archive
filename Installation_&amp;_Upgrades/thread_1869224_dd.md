---
title: "dd"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by Krabs on 2011-10-25
I'm having some problems with erasing my drive. First I erase my drive with this command 

[FONT=Courier New]dd if=/dev/zero of=/dev/sda bs=1M[/FONT]
 
Next for security reasons with encryption they said to run this command:
 
[FONT=Courier New]dd if=/dev/zero of=/dev/urandom bs=1M[/FONT]
 
But when running this command, my hardrive(500G) seems to be in a loop.
 
I googled on internet, how to see dd's OUPUT:
 
The OUTPUT : (17TB)? copied, 274932 s , 62.4MB/s
Is it normal that it lasts that long? 76.37 houres!

---

### Post by matt_symes on 2011-10-25
Hi

> **Krabs said:**
> I'm having some problems with erasing my drive. First I erase my drive with this command 

[FONT=Courier New]dd if=/dev/zero of=/dev/sda bs=1M[/FONT]


This will erase your hard drive by writing zero's onto your hard drive sda.

>  
Next for security reasons with encryption they said to run this command:
 
[FONT=Courier New]dd if=/dev/zero of=/dev/urandom bs=1M[/FONT]


Where did you get this command to run from ? It is not touching your hard drive but writing zero's to urandom.

> 
But when running this command, my hardrive(500G) seems to be in a loop.
 
I googled on internet, how to see dd's OUPUT:
 
The OUTPUT : (17TB)? copied, 274932 s , 62.4MB/s
Is it normal that it lasts that long? 76.37 houres!

It's not writing to your hard drive at all.

Kind regards

---

### Post by psrdotcom on 2011-10-25
You can try the same command with Live CD ..

Boot from Live CD/USB and try to format the disk with ZEROs.

---

### Post by docbop on 2011-10-25
Even simpler download a copy of DBAN  (Derick's Boot And Nuke) and burn it to a CD.   It's a bootable Linux with multiple options for securely wiping hard drives.   You can also start it and eject the CD and leave it to finish.

---

### Post by Krabs on 2011-10-25
@matt_symes
Where did you get this command to run from ? It is not touching your hard drive but writing zero's to urandom.
 
From an arch forum. 
I do now realize that it couldn't work, 'cause the LED-lamp of my hard disk wasn't burning and so, it couldn't write data. 
Thanks alot for your help. 
PS: I just changed the command from if=/dev/zero of=/dev/urandom bs=1M to if=/dev/urandom of=/dev/sda bs=1M

---

### Post by matt_symes on 2011-10-25
Hi

> From an arch forum. 

The Arch wiki and forums are generally a pretty good resource when one understands the differences between Ubuntu and Arch. I have been using them today myself.

I think in this case the poster on the Arch forum may have made a typo.

I'm glad it's fixed :)

Your changed command looks much better if you want to write random data to the hard drive. It will still take a while though with no feedback unless it fails.

Kind regards

---

