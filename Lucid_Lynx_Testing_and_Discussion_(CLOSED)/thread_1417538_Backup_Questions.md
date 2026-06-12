---
title: "Backup Questions"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by stevedude on 2010-02-27
I'm new to Linux and started using Ubuntu around 6 months ago and I am loving it. I am still however, new to this system and I would like to tap into someone's know-how about backups. I am currently running Ubuntu Karmic Koala 9.10.

I want to prepare for the upcoming Ubuntu Lucid Lynx 10.04 LTS. I have literally spent months getting my system to look the way I like it and install many programs that I use on a daily basis. My concern is when I upgrade to 10.04, I will lose all of my visual settings (I am using Compiz-Fusion) and other miscellaneous things like all of my music tags that I use in either Amarok, and Songbird.

I have researched this and found "Back in Time", "FWbackups", and "APTonCD".

Can anyone tell me if anyone of these will do what I want to keep my program and visual settings? Is there something out there I have missed that will do a better job? Are there other steps I need to take to prepare for Lucid 10.04?

Please remember I am a newbie and prefer something that is GUI based, in lieu of that, any other recommendation that is terminal based will have to have a good website instruction in order for me to follow it :-)

Thanks so much in advance for any help any of you can share!

---

### Post by Pollox on 2010-02-27
I think your best option is to just use Update Manager to upgrade to Lucid when it comes out.  This works just like any other time you update packages with Update Manager.  It won't remove any files, settings, or programs you installed.

Still, doing backups is a good idea, especially before updating to a new version of Ubuntu (just in case something goes wrong).  I like "Back in Time" for this, but there are many good options in the repositories.  You could just copy/paste stuff to an external drive, but programs like Back in Time should be quicker because they only copy over files that have been modified since your last update.

Now, what to back up exactly?  Well, your files and most program settings are stored in your home folder (e.g. /home/pollox).  Your list of installed programs is a little trickier.  I use Synaptic: go to file >> save markings, and check the box "save full state, not only changes".  I also back up /usr/local, /etc, and /var, with some exclusions.  Actually, I just took the default settings from "sbackup" and entered them in "Back in Time".

If you're interested more in backup options, there's plenty of threads on it in these forums, or perhaps someone more knowledgeable will chime in here.

---

### Post by stevedude on 2010-02-28
Thanks Pollox for the reply and sharing ideas of what to backup. I actually got in on the tail-end of Jaunty and used Upgrade Manager to upgrade to Karmic. I did lose some data with upgrading via that method, especially painful was all of my music tags. I didn't want to repeat that mistake so anyone that has suggestions - I am all ears.

Thanks again for the input.

---

### Post by cjhabs on 2010-02-28
I know this is isn't related to your question, but you lost your music tags when upgrading???
Are you sure it wasn't a problem with the updated music program not reading the tags the same way anymore? I can't imagine how losing the tags could happen.
There are assorted tag versions available, for example, in mp3 files - I wouldn't expect an update to touch your data (maybe some dot files)

---

### Post by stevedude on 2010-03-02
cjhabs, I believe the upgrade at that time changed both Amarok and Songbird, which are the 2 music programs that I use. They were probably program updates along with the upgrade from Jaunty to Karmic. Anyway, I did lose my tags and associated album covers and had to input the data by hand.

I just want to be smarter about upgrading the next time and Pollox gave me some great tips and I'll do some more research about what directories I should back up. 

I just want to cover all of my bases in case I upgrade and I experience a less-than-perfect installation.  I've spent so much time getting the system to look and run like I want it and being a newbie, if I experience some issues, it takes me a lot longer to figure things out.

I do want to say this, the support for Ubuntu is fantastic, and I am loving running Ubuntu as my desktop replacement to Windows 7. Six-plus months of running it and NO reboots or system freezes!

---

