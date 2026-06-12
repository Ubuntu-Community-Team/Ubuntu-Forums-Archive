---
title: "Can i clone my Ubuntu install?"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by Macfunky on 2010-01-29
I want to be install ubuntu onto another computer but i would like to have it set up exactly like my main desktop. It wouldn't take a huge amount of time but it would make it so much easier if i could just clone it. Is there any way i could do this? Perhaps put it on a disc with every setting as i have it and additional software etc. Any ideas?

---

### Post by MelDJ on 2010-01-29
see: [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by doas777 on 2010-01-29
well, cloning will require that both pcs have exactly the same hardware, so that is a little tricky in an hetorogenous environment. if both boxes are the same, look into partimg.
if they are differant however, you can still get almost all the settings customized automatically, by copying your home directory to the new pc. most of the desktop and user settings are stored there.

---

### Post by lavinog on 2010-01-29
> **doas777 said:**
> well, cloning will require that both pcs have exactly the same hardware, so that is a little tricky in an hetorogenous environment. if both boxes are the same, look into partimg.
if they are differant however, you can still get almost all the settings customized automatically, by copying your home directory to the new pc. most of the desktop and user settings are stored there.

That isn't true.
You shouldn't have any problems with cloning the install if the hardware is different, unless you installed a proprietary driver like fglrx or nvidia

---

### Post by elliotn on 2010-01-29
when i moved my hard drive from a p3 with 8.10 to my current pc ubuntu worked without any conflict so i guess cloning would work too

---

### Post by doas777 on 2010-01-29
> **lavinog said:**
> That isn't true.
You shouldn't have any problems with cloning the install if the hardware is different, unless you installed a proprietary driver like fglrx or nvidia
or a wifi card, or an 3com nic, or any number of other internals. just the ACPI implementation may make the image unbootable on new hardware. 

op to clarify, it is possible, but can be fraught with peril. if, like Sir Galahad the Chaste, you can deal with a little peril, then the castle anthrax is right for you.

"bad zute. naughty, naughty zute. she must be punnished." --Carol Cleveland

---

### Post by Sef on 2010-01-29
>  Is there any way i could do this? Perhaps put it on a disc with every  setting as i have it and additional software etc. Any ideas?, 

Yes.  Check out [clonezilla]("http://clonezilla.org").

---

### Post by realzippy on 2010-01-29
I think remastersys could do the job.

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

it works great.

---

### Post by oldfred on 2010-01-29
I think the suggestions already given would work. For me I had recently installed Karmic to my desktop and was having issues getting Samba to work to my laptop, so I installed Karmic to my laptop. I considered the laptop enough different that I could not clone it. And I use my laptop more as another desktop when away from home.

I had saved the commands I used to configure my desktop from listing history at command line. That gave me many of the special things I installed with sudo apt-get install or wget. Make sure all PPA or additional sources are added. I then listed all the packages I had installed (some already reinstalled) with 
dpkg --get-selections | grep -v deinstall > ubuntu-files
and reinstalled then. I copied most of /home over and was all set. 

I saved everything initially as I wanted it for my next install so I had a record of all the settings/programs I had installed.
Using NFS was a lot easier than getting Samba to work and now I have not gone back into windows on my portable.

---

