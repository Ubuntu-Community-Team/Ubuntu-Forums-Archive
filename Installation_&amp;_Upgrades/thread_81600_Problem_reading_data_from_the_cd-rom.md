---
title: "Problem reading data from the cd-rom"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by MAXCC0012 on 2005-10-24
hi everybody....

I just tried to install ubuntu-5.10-install-amd64.iso...  but it doesnt work... the installation aborts with the following error: There was a problem reading data from the cd-rom. please make sure that the cd-rom is in the drice....
If retrying does not work you should check the integrity of your cd-rom...

First I thought that the cd-rom was  bad... and i burnt another one... and checked the integrity of the data after it had been burnt... then I tried again... with the same problem... then I thought that the package I have downloaded may be corrupt.... so I checked md5-hash of the iso... and it was correct....arrrgg... the cd-rom drive works perfectly under windoze... and up to now i have burnt three cds... but none of them worked...

EDIT: I checked the integrity of the cd-rom drive (there was an option in the installation)  the result: the cd-rom drive is OK... 

why is linux doin that to me????

Any help is greatly appreciated!!!

 thx in advance

---

### Post by tiefling on 2005-10-24
What kind of CD-ROM drive do you use to boot up with? Brand, model, etc...

---

### Post by MAXCC0012 on 2005-10-24
[QUOTE=tiefling]What kind of CD-ROM drive do you use to boot up with? Brand, model, etc...[/QUOTE]

plextor-740a

I forgot to mention that the installation starts normally....and aborts somewhere after the beginning (load installer-components from cd [<-my translation])

---

### Post by peebee on 2005-10-24
[QUOTE=MAXCC0012]plextor-740a

I forgot to mention that the installation starts normally....and aborts somewhere after the beginning (load installer-components from cd [<-my translation])[/QUOTE]

You may want to try reburning the CD at a lower speed.

I have had issues like this, where it would also go through the install and crash out at various stages. and the above worked for me.

---

### Post by MAXCC0012 on 2005-10-24
But i have burned it three times (two times with 48x) and one time with 36x and I compared the iso and the content of the cd-rom after i burnt it and nero said that it was successful....? Or should I burn it with even lower speed than 36x???

---

### Post by taurus on 2005-10-24
I would take about 20 minutes but I think you should consider burning it at 4x!!!

---

### Post by tiefling on 2005-10-24
[quote=MAXCC0012]plextor-740a

I forgot to mention that the installation starts normally....and aborts somewhere after the beginning (load installer-components from cd [<-my translation])[/quote] 
More or less the same drive as my BenQ 1640...

Use expert mode (just type 'expert') and when asked for a hdparm parameter for your CD/DVD-drive type in '-d1'. I don't remember exactly when it asks.. think it was right after it mounts the drive. Just read the dialogues carefully.

This drive needs DMA, and for some reason it doesn't get enabled by default in Ubuntu.

*Edit:* And, just to add, you're usually better off burning your CDs and DVDs at the lowest speed possible. Burn at too fast a rate and there's bigger changes of errors (that the burning software won't neccessarily detect).

---

### Post by TryAFrog on 2005-10-25
I've been having a similar problem and have been burning @ 4x, and even tried 2x, any suggestions? Is it possible to do a network install???

---

### Post by MAXCC0012 on 2005-10-25
[QUOTE=tiefling]More or less the same drive as my BenQ 1640...

Use expert mode (just type 'expert') and when asked for a hdparm parameter for your CD/DVD-drive type in '-d1'. I don't remember exactly when it asks.. think it was right after it mounts the drive. Just read the dialogues carefully.

This drive needs DMA, and for some reason it doesn't get enabled by default in Ubuntu.

*Edit:* And, just to add, you're usually better off burning your CDs and DVDs at the lowest speed possible. Burn at too fast a rate and there's bigger changes of errors (that the burning software won't neccessarily detect).[/QUOTE]
thx for your reply 

but i couldn't solve the problem: I used expert mode - but the installation didn't ask for hdparm parameter for my CD/DVD-drive. 
The only thing I found was an option for additional parameters for kernel modules. but none of them accepted  the parameter -d1...
plz help me!
where can I enter this parameter....
im REALLYZ fed up with this installer-shit.... I burnt 5 cds the installer crashed 20 times... and in the end it doesnt work.... this reallz starting to suck....  
plz help...

---

### Post by peebee on 2005-10-25
I burnt mine at 4x and it is fine, it didnt take 20 minutes either.

---

### Post by MAXCC0012 on 2005-10-25
mine is not working...i burnt it with 12x which was the f***ing lowest speed that i could choose in nero! and its still NOT WORKING...and it sucks....!!!!

---

### Post by tiefling on 2005-10-25
[QUOTE=MAXCC0012]mine is not working...i burnt it with 12x which was the f***ing lowest speed that i could choose in nero! and its still NOT WORKING...and it sucks....!!!![/QUOTE]

It's a DMA issue. You can keep burning 'til you run out of discs, but it won't change anything.

Here's a mini-walkthrough up to the critical point:

- Boot with 'expert'
- Choose language
- Choose location
- Choose Locale
- Add more locales if needed
- Choose keyboard layout
- Detect and Mount CD
- Leave as-is, don't touch anything, just Continue
- Choose "No" when asked for module parameters
- Choose "No" when asked for PC card services (unless you need it)
- You should get a window now that, among other things, include the text
"Tune CD-ROM drive parameters with hdparm?"
- Enter '-d1' in the textbox then Continue

That's it.

---

### Post by MAXCC0012 on 2005-10-27
[QUOTE=tiefling]It's a DMA issue. You can keep burning 'til you run out of discs, but it won't change anything.

Here's a mini-walkthrough up to the critical point:

- Boot with 'expert'
- Choose language
- Choose location
- Choose Locale
- Add more locales if needed
- Choose keyboard layout
- Detect and Mount CD
- Leave as-is, don't touch anything, just Continue
- Choose "No" when asked for module parameters
- Choose "No" when asked for PC card services (unless you need it)
- You should get a window now that, among other things, include the text
"Tune CD-ROM drive parameters with hdparm?"
- Enter '-d1' in the textbox then Continue

That's it.[/QUOTE]

Thx....

I found out what the problem was... This dialog (where you can set the drive-parameters) doesnt appear in the AMD64 installation...!!! the AMD64 always ended with an error (about cd-rom drive)  .... When I tried the 386 release the dialog appeared...  and I entered the  '.-d1' - parameter and I was able install ubuntu successfully!!! THX!!!

is this  bug known????

---

### Post by wize_guy123 on 2006-01-19
I have a similar problem.. I got some Ubuntu 5.10 discs from ShipIt, and I've tried the PC version and PC-64 version, but the discs aren't read. They just sit in the drive, and the light just sits on green.

---

### Post by StreLochKi on 2008-02-05
7.10 server
I have the same problem on a Dell poweredge 2550
but i don' get the dialog or i don't get into that expert mode

op my desktop, the integrity is good
on the server the integrity fails, and than he starts asking questions:
check the integrity of another cd-rom? No
Insert Ubuntu boot cd-rom. (was in all the time) Continue
PCMCIA ressource range options: -d1 enter (not continue)
! then i get the hdparm dialog box!
Tune CD-ROM drive parameters with hdparm? -d1
than he rescans the cdrom and says "The cd-rom autodetection was successful. A cd-rom drive has been found and it curently contains the CD Ubuntu server 7.10 "Gutsy Gibbon" - release i386 (20071016). The installation will now continue. Continue
than I get the same menu after the first crash, I continue the installation, and crashes again

---

### Post by Rounan on 2008-03-12
I am having the same problem on the same hardware (Dell Poweredge 2550), using Ubuntu 7.10 server.

Has anyone found a successful workaround?

---

### Post by HeadGremlin on 2008-05-05
While not the best solution I have found that the Minimal CD will allow you to get the system working.  You can get it from:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

The minimal cd's drawbacks are:

1.  Must have internet access

2.  It can be a slow process if your speed it not good.

3.  I generally don't like attaching my servers to the internet until I get them a little more locked down.  This issue makes a clean network with a well configured firewall a must for security reasons.   

Specifics:
I am installing the software on an Dell Power Edge 2550
Both the 8.04 server and 8.04 alternate versions fail
The CD's work fine in other machines and even newer Dell servers
Replacing the CD-rom drive with a newer one does not fix the problem
Bios will not allow for installs from USB attached CD/DVD-roms
I only tested the install with the "cli" argument (Command line only) 

I hopes this helps someone.

---

