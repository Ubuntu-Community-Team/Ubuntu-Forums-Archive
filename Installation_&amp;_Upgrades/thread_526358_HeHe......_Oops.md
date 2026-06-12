---
title: "HeHe...... Oops"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2007-08-15
This was a REALLY dumb move on my part, but what can I say, I was a little tired at the time. Here is the situation. I was in a pissy mood because I couldn’t get my desktop effects to work. So my wonderful solution was to uninstall the NVIDIA drivers I had gotten off of Automatix (using automatix to uninstall them). I rebooted my computer, the splash screen went well, but after that, the screen went dark. I assume this is because I made the genius move of uninstalling the drivers without replacing them first, so Ubuntu is trying to load drivers that are not there. Is there a way to make it so I can get at least the gui going so that I can reinstall the drivers? I know when I first installed Ubuntu it used the NVIDIA drivers that came with it, there was no 3d, but it was usable. Thank you so much for putting up with a moron.

---

### Post by jim_p on 2007-08-15
Can you boot into recovery mode?
Or even into text mode? (the one that looks like a command prompt)
If so, you have to alter /etc/X11/xorg.conf with some text editor and replace all "nvidia" entries with "nv".
This will roll back to ubuntu's default nvidia driver.

If you can't boot into recovery or text mode, use a live cd to do the changes ALWAYS AS ROOT.

Reboot and reinstall the drivers again from scratch.

---

### Post by ErusGuleilmus on 2007-08-15
No CLI. I&#8217;ve never heard of using a live CD to do the changes. Will it automatically pick up my Ubuntu partition? I dual boot Vista w/ Ubuntu so will that cause any problems? With the Live CD, do I just treat it as if everything is normal and install the drivers, or do I need to point to where the driver should install? Thanks.

---

### Post by jim_p on 2007-08-15
Yes. You shouldn't have any problems with the live cd.
Your Linux partition is most likely formated in ext3 so it will be readable at once.
If not, you will be able to find your drive's folder structure inside /media/hda0 or something like that.
(inside the /media folder anyway)

Don't forget to use the root account to alter the file!

---

### Post by ErusGuleilmus on 2007-08-15
Will I just be able to run Automatix and install the drivers like normal?

---

### Post by jim_p on 2007-08-15
After you boot to your Linux installation? Surely, why not!?

If you install drivers and automatix while in the live enviroment, they will be gone once you reboot your pc.

---

### Post by ErusGuleilmus on 2007-08-15
I realize this. What IM trying to say is that I have no idea as to manually install drivers form the live cd to the copy on my hardrive. If I cant just run automatix on while on the live cd and install the drivers to the right directory on the HD, I will have no other idea on how to do it. Sounds like Ill be better off just reinstalling Ubuntu all together.

---

### Post by jim_p on 2007-08-15
Lets seperate 2 things.

You use the live cd to correct that file, to do that editing that HAS to be done.
After that, the live cd's part is done. You may reboot and put it aside. 

Afterwards, you will boot to your Linux as if nothing happened and reinstall the drivers
from anywhere you wish.

I can guide you if you think you will make a mess.
I have tried all 3 ways of installing drivers (automatix, synaptic, straight from nvidia).

The thing is that i will be home for the next 30 minutes max :(

---

### Post by ErusGuleilmus on 2007-08-15
Then I will need instructions on how to edit the neccasary files from the live cd so that I can boot in as if nothing happened.

---

### Post by jim_p on 2007-08-15
Ok. Boot from the cd and I will wait.
I will pm you my email now

---

### Post by ErusGuleilmus on 2007-08-15
Does any body else know what editing needs to be done from the Live CD? If so, could you please tell me? I have no idea when this other guy will be back on, and some files I have on there are moderately critical.

---

### Post by jim_p on 2007-08-15
What other files do you wish to edit?
I think that the /etc/X11/xorg.conf file is enough.
You will just revert to the old drivers and thats it.
I know that the settings in there are critical but this is the only way to go.

I just saw in my installation that a backup copy of the file exists next to the original with a  ~  as a suffix.
You may want to check the differences between the two if you hesitate to edit

---

### Post by ErusGuleilmus on 2007-08-15
What do I need to edit in the /etc/X11/xorg.conf from the live CD to get it to run the basic nvidia drivers?

---

### Post by jim_p on 2007-08-15
As i said earlier 
> If so, you have to alter /etc/X11/xorg.conf with some text editor and replace all "nvidia" entries with "nv".
This will roll back to ubuntu's default nvidia driver.

---

### Post by ErusGuleilmus on 2007-08-15
Sorry for being a pain in the ***. Im a little tired today.

---

### Post by jim_p on 2007-08-15
Its ok. I dont mind. 
Everyone can have his ups and downs
Tell me when you are done

---

### Post by ErusGuleilmus on 2007-08-15
you are a God among men! I opened the file and found that there was an "nv" instead of an "Nvidia" i changed it to nvidia and it works, thank you!!

---

### Post by craigsharp on 2007-08-15
All of that wasn't completely necessary.  Yes you did get it working, but for future references your can log in to text mode and enter

```
sudo dpkg-reconfigure xserver-xorg
```

This will correctly reconfigure your xorg.conf file.  You might save this post just in case you or somebody else messes up their xorg.conf file.

---

### Post by Blindraven on 2007-08-16
Be carefull not to mention Automatix if you have issues related moreoso to you then the script or you will give people the fuel they need to continue their issues against it *sigh*.

---

### Post by jim_p on 2007-08-16
> I opened the file and found that there was an "nv" instead of an "Nvidia" i changed it to nvidia and it works, thank you!!

Thank you for the nice words.
I am glad to hear it worked.
I still think that mine is the other way round.
Tell me if you need any help

---

