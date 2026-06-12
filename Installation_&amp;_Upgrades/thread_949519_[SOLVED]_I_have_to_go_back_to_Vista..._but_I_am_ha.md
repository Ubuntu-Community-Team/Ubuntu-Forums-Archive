---
title: "[SOLVED] I have to go back to Vista... but I am having problems"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by camputer on 2008-10-16
I have to go back to Vista... My Lenovo Thinkpad SL400 runs a lot better on Vista, Ubuntu has just been problems from day one (think because this is a relatively new model of Lenovo computer).

Now when I try to go back to Vista when I start the installation process it says that Hard drive drivers can't be found... I went to the hard drive manufacturer's website and it says there that the drivers are already preinstalled on the drive...

 

Vista won't allow me to continue with installation until I can get those drivers and select proper partitions.

 
According to Windows help site: [http://support.microsoft.com/kb/927520]("http://support.microsoft.com/kb/927520")

 

I think my only option is method 8 and completely format the drive and see if windows detects it then... think this is a good idea?

 
Does the Fact that I have Ubuntu on here prevent Windows from finding the harddrive drivers?

I realize I am asking for Vista help on the Ubuntu forum, but I figure I will get better support here than elsewhere and Ubuntu is what I am working with right now.

Any help is appreciated.

---

### Post by BenAshton24 on 2008-10-16
hmm.. you could give it a shot completely formatting it (if so i suggest formatting it to NTFS with the [Parted Magic]("http://partedmagic.com") live cd) the fact that the drive is currently formatted in ext3 could be the reason that you can't install vista. But noooooo! don't leave Linux! especially for vista :( try some other distros and stick with it for a bit, eventually you will see that it's miles better than anything microshaft (excuse the typo :P) has ever coughed up :P

Hope this helps,
Ben.

---

### Post by camputer on 2008-10-16
Thanks so much for the quick reply!

I know what you mean, I love the customization of ubuntu and all the great Compiz effects and the fact that I am pretty safe from adware-spyware-malware-viruses etc... 

but the fact that none of my sweet thinkpad function keys work, the volume buttons don't work, I can't suspend or hibernate, my brightness down button turns the brightness up (up turns it down). I had to work like a dog to get my wireless working, Half the time Ubuntu doesn't recognize my graphics card right and messes up the resolution. Videos freeze my screen...

I just want to go back to the way the computer came, I will miss the features of Ubuntu though!

Thanks again, I will try what you suggested today and let you guys know how it worked (or didn't).

I just don't want to be stuck with a blank HDD with no OS.

---

### Post by caljohnsmith on 2008-10-16
> **camputer said:**
> 
Now when I try to go back to Vista when I start the installation process it says that Hard drive drivers can't be found... I went to the hard drive manufacturer's website and it says there that the drivers are already preinstalled on the drive...
When you installed Ubuntu, did you leave your Vista partition and/or the recovery partition on the HDD? Or did you completely replace Vista with Ubuntu? Before you format, how about posting:
```
sudo fdisk -lu
```

---

### Post by camputer on 2008-10-16
Too late, I allready completely cleaned the drive using diskpart.exe, clean all, (off the windows CD).

After that I pressed refresh on the partition selection screen and Windows was able to install.

Thanks to everyone for their interest and help, I am glad I was able to figure this out! 

I wont forget ubuntu... It may very-well be the way of the future. But as a student at University, Vista is just more practical.

---

