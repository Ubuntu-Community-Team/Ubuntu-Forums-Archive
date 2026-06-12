---
title: "Really Messed Up This Time"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by puner on 2007-06-02
I wanted to remove Ubuntu 7.04 from my other hard disk, so what i did is i went into my disk settings in WinXp and formated the disk until there was nothing on there.

Now when i boot my computer i get this; 

[http://imagenerd.com/uploads/dsc00038V5Ug.jpg](http://imagenerd.com/uploads/dsc00038V5Ug.jpg)

I cant even re-install ubuntu either.

Before when everything was fine, i had Ubuntu 7.04 as my main OS and WinXp as my "Other install OS's".

So what can i do?

---

### Post by PilotJLR on 2007-06-02
Use your WIndows CD to boot to the Recovery Console, then run the "fixmbr" command.
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

This will remove Grub and install the Windows MBR.

---

### Post by puner on 2007-06-02
> **PilotJLR said:**
> Use your WIndows CD to boot to the Recovery Console, then run the "fixmbr" command.
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

This will remove Grub and install the Windows MBR.

Am i in the risk of loosing any data?

---

### Post by PilotJLR on 2007-06-02
> **puner said:**
> Am i in the risk of loosing any data?

From the fixmbr command alone, no.

If you deleted anything else previously, then of course it's possible.


Stick to ONLY the fixmbr command, and it should only touch the boot record and not any specific partition. Search the threads for fixmbr and you'll see many instances of this.

---

### Post by puner on 2007-06-02
> **PilotJLR said:**
> From the fixmbr command alone, no.

If you deleted anything else previously, then of course it's possible.


Stick to ONLY the fixmbr command, and it should only touch the boot record and not any specific partition. Search the threads for fixmbr and you'll see many instances of this.

Ok, so i tried the recovery mode and i was brought to this screen;

[http://imagenerd.com/uploads/dsc00041Dag4.jpg](http://imagenerd.com/uploads/dsc00041Dag4.jpg)

after that i press enter (like it says) and nothing happens, i just get rebooted.

Also when i pop in the LiveCD i can get to the Live desktop. From there i cannot install linux again, because it doesnt see my external drive. And i dont want to install on my main drive either.

---

### Post by bulldog on 2007-06-02
> **puner said:**
> Ok, so i tried the recovery mode and i was brought to this screen;

[http://imagenerd.com/uploads/dsc00041Dag4.jpg](http://imagenerd.com/uploads/dsc00041Dag4.jpg)

after that i press enter (like it says) and nothing happens, i just get rebooted.

Also when i pop in the LiveCD i can get to the Live desktop. From there i cannot install linux again, because it doesnt see my external drive. And i dont want to install on my main drive either.

You should type 1 and then enter,it will ask for your administrator password.

If you install Ubuntu onto an external hdd,I assume you can boot from an external hdd,you should install GRUB on the external hdd too.
So you only see GRUB when you boot from the external hdd,otherwise you will boot your windows.

---

### Post by puner on 2007-06-02
> **bulldog said:**
> You should type 1 and then enter,it will ask for your administrator password.

If you install Ubuntu onto an external hdd,I assume you can boot from an external hdd,you should install GRUB on the external hdd too.
So you only see GRUB when you boot from the external hdd,otherwise you will boot your windows.

Problem is that i cant boot from the external drive. I formated it from WinXp so there is nothing on there. 

So now when i boot up, my computer tries to find Linux, and since there is nothing on there im getting the error.

I want to make my computer understand to boot Xp from now on, because there is no Linux any more.

---

### Post by bulldog on 2007-06-02
Yes,I understand all that :p
You should go into recovery console from the windows install disk.
You did this already but instead of enter you should type 1 and then enter,then provide your administrator password.
Then you can type fixmbr and fixboot.
This will remove GRUB from the MBR and all should be fine again.

---

### Post by puner on 2007-06-02
> **bulldog said:**
> Yes,I understand all that :p
You should go into recovery console from the windows install disk.
You did this already but instead of enter you should type 1 and then enter,then provide your administrator password.
Then you can type fixmbr and fixboot.
This will remove GRUB from the MBR and all should be fine again.

Will try :)

---

### Post by puner on 2007-06-02
> **puner said:**
> Will try :)

Ok, so i wrote "fixmbr"

and then i got this long warning;

[http://imagenerd.com/uploads/dsc00045BgAe.jpg](http://imagenerd.com/uploads/dsc00045BgAe.jpg)

I'm not sure this is the right way, because Linux wasn't even installed on a new partition, it was installed on a new hdd itself.

So should i go ahead and create a new MBR?

---

### Post by bulldog on 2007-06-02
Yes,it's a standard warning.
In 99,9% it's going without any problem so don't worry about that.
Don't forget the fixboot command.

---

