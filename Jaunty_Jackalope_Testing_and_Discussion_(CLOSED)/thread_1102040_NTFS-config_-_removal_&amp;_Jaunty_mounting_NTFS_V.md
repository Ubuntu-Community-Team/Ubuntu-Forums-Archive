---
title: "NTFS-config - removal &amp; Jaunty mounting NTFS Vista drive???"
date: 2009-03-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dBuster on 2009-03-21
Okay back a few months, okay maybe it was just two months ago, but none the less mounting a NTFS drive was not working with earlier Alphas.  So the work around was to install NTFS-Config.  I did that and every time I reboot it mounts the drive and puts an icon on the desktop.  I do not mind it mounting each time, what I do mind is the icon on the desktop.  

My questions being:

1.  Is the current Alpha able to mount a NTFS drive without any work arounds?  If so how?

2.  I know this is going to sound like a noob question, however my mind is not recalling how I can remove the NTFS-Config if there is another alternative in Jaunty.

3.  If I am having to retain NTFS-Config, is there a way to have it not mount automatically or display an icon on the desktop?

I know lots of questions there.  Searching doesn't return much regarding ntfs and jaunty...

Or any other ideas???

---

### Post by Bert Mariën on 2009-03-21
If you change the /etc/fstab file for yoiur mounted or unmounted devices like this

/dev/sda1 /media/test ignore 0 0

dev/sda1 won't show up on your desktop.

---

### Post by Bert Mariën on 2009-03-21
Do that for al the devices you do not want to see on your desktop, and you'll be okay.
(I think.)

---

### Post by Bert Mariën on 2009-03-21
You won't see them, but I cannot tell whether they are mounted...
You have to figure that out yourself.

---

### Post by chrisccoulson on 2009-03-21
NTFS automounting should be working ok in Jaunty now, and should have been for some time. The (unmounted) drive should appear in computer:///. Just double click on the drive in Nautilus, and it should mount without any issues with the ntfs-3g driver now. No need for messing around with fstab, unless you want your NTFS drive as a static mount.

---

### Post by dBuster on 2009-03-21
> **chrisccoulson said:**
> NTFS automounting should be working ok in Jaunty now, and should have been for some time. The (unmounted) drive should appear in computer:///. Just double click on the drive in Nautilus, and it should mount without any issues with the ntfs-3g driver now. No need for messing around with fstab, unless you want your NTFS drive as a static mount.

So if it is working now any idea if I need to add a package for ntfs-3?

How about removing the ntfs-config?  Wouldn't that be a simple sudo apt-remove ntfs-config?

Been a long day and the command line verbage is escaping me now...

---

### Post by nystire on 2009-03-21
Use "sudo apt-get purge ntfs-config" to remove the package and all it's configuration files. Just check what it tells you before agreeing to anything so that you don't end up killing anything else :)

NTFS-3G should be installed by default. You shouldn't have to do anything special to use the NTFS drive.

---

### Post by henwyn on 2009-03-22
Open up the synaptic package manager. The ntfs-3g package should already be installed. If it isn't, mark it to install. The next package is ntfs-config; right click it and mark it for removal. While you're at it, reload your sources and mark all updates. Then hit apply. Should take care of you.

---

### Post by dBuster on 2009-03-22
> **henwyn said:**
> Open up the synaptic package manager. The ntfs-3g package should already be installed. If it isn't, mark it to install. The next package is ntfs-config; right click it and mark it for removal. While you're at it, reload your sources and mark all updates. Then hit apply. Should take care of you.

Okay that is weird...  I open the package manager and in the search I put ntfs just like that.  I get only two options, "ntfsprogs" and "ntfsdocs" and that is it.  I click on community maintained and there is the "ntfs-config".  

No where do I see the ntfs-3g...  I wonder if I am missing a repository in my list...  I will install from their website and see how it goes.

Okay that was even weirder...  I just did a sudo apt-get install ntfs-3g and was told after already removing ntfs-config, that I am at the most recent release.

Went to edit the fstab and the vista drive is there...  hmmm but trying to pull it up in say nautilus with or without root access and it is not there.  not mounted...  Going to reboot and see what happens.

---

### Post by dBuster on 2009-03-22
Okay just back from reboot.  System seems to reboot a lot faster without the ntfs-config.  Could be my imagination...  Wait let me check bootcahrt. ;)

Okay bootchart shows same boot time...  34s

Still have the icon on the desktop.  Will try to do that setting to remove it from the desktop see if that works for what I am trying to accomplish.

---

### Post by dBuster on 2009-03-22
Boy do I feel like a fool...  It was so simple to remove those icons from the desktop and still retain the mounts.

[tuxtraining -quick-how-to-hide-mounted-drives-on-gnomes-desktop]("http://tuxtraining.com/2008/07/13/quick-how-to-hide-mounted-drives-on-gnomes-desktop/")

It was simple...

Just type in gconf-editor into the Alt+F2 run dialog to open the app or your terminal.

Now browse down to the following key:

apps \ nautilus \ desktop

Find the "Volumes_visible" entry and remove the checkmark.  As soon as you remove it the icons on the desktop are poof gone yet you retain the mounts. 

DUH... 

Thanks all for the help on this.  See what happens when I get some coffee I figure things out.

---

