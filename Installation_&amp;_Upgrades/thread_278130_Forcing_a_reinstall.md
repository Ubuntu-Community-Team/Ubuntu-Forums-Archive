---
title: "Forcing a reinstall"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by racsw on 2006-10-15
I've run into a problem with Ubuntu 6.06.  I installed the Kubuntu Desktop just to see how it works, and now I can't delete it, using apt-get or Synaptic.  It's like a virus that won't go away.  It was originally installed using apt-get.
  I'm trying to return my system to original Ubuntu with the 6.06 Version.  The only way I can do this without reformatting and starting over is to do another install, but force overwrites in all cases.
  Hopefully, that will overwrite any configuration files that have been modified that are responsible for bringing up the Kubuntu Login screen, which I have repeatedly tried to delete.
  If anyone has the correct sysntax to install and overwrite, I would appreciate it.
  Similarly, if someone has a clue to where that Kubuntu login screen is being called from, I might be able to delete that also as an extra measure of insurance.
  Short of this, the last step is to reformat and reload, which I have no problem with other than hours of reinstalling programs.

Regards,
Robert

---

### Post by NeoLithium on 2006-10-15
sudo apt-get remove kubuntu-desktop doesn't work...how did you initially install it, and what type of errors are you getting?

---

### Post by racsw on 2006-10-16
You are correct. I used "sudo apt-get install kubuntu-desktop" to install.
I used "...remove..." to uninstall.
When I turn on the computer, I get the Kubuntu Blue logo and name, while the boot messages are scrolling up.   Then I am brought into the Kubuntu login screen, where I am forced to select Ubuntu.  I can't remember how to select auto-login in Ubuntu, but I should not have to do it if Kubuntu is not there.

I have also removed "kde", in a effort to fix this, but now I have other small problems.  I simply want to return my system back to it's original Ubuntu default state, with no trace of Kubuntu, and auto-login.

Thanks,
Robert

---

### Post by bulldog on 2006-10-16
Select another spash in Administration--login-screen.

Think this wil solve your problem.

And when you choose Ubuntu as a default when you login it should stick.

---

### Post by racsw on 2006-10-16
Only problem is...my Administration-->Login doesn't work.
The little wheel goes around, but dissaperas with no Login GUI.
I think it was part of this problem that was created when Kubuntu was loaded.
It used to function, but no longer does.
How can I get it back?

Thanks,
Robert

---

### Post by bulldog on 2006-10-16
Take a look here,maybe you find something usefull.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by ahaslam on 2006-10-16
> **bulldog said:**
> Take a look here,maybe you find something usefull.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

That'll do it :)

 it'll be wise to use aptitude for such future installations ;)

Tony.

---

### Post by racsw on 2006-10-16
Well, I thank you for your help, but it didn't work.
I copied and pasted the entire command, it did it all, and on reboot, it says "Welcome to Kubuntu Robert-desktop".

Now what??

Robert

---

### Post by bulldog on 2006-10-16
Try to reinstall your Ubuntu desktop.
```
sudo aptitude install ubuntu-desktop
```

---

### Post by racsw on 2006-10-16
I gave up.  I don't have time to keep screwing with this.
I reformatted and reinstalled Ubuntu.
Evereythings working correctly, and now a few hours of time is required to get things back the way they were.
I would strongly suggest to users NOT to try loading Kubuntu unless they plan to keep it.  Removing it completely is not an option.

Thanks,
Robert

---

### Post by ahaslam on 2006-10-17
I found a nice little app yesterday, enabling me to free up 286MB worth of orphaned dep's. It's called Gtkorphan & it's in the repo's, full credit goes to Aysiu.

If you use aptitude, the need for this will be minimal, but sometimes it's just convenient to use Synaptic ;)

You shouldn't have to re-install to fix minor problems, I'm running an upgraded Breezy install & I'm still a noob ;)

Tony.

---

### Post by gigaferz on 2007-01-12
Right now I am in the same situation,
after the kubuntu addition, sometimes it takes to 6 minutes to boot..

I think my unistallation will be ok..

Everything started when I started removing applications wich they have no use at all. because I have the gnome versions.. Then I killed a process and kubuntu went crazy, sometimes when I reboot it show me that it missing some media files..or something like that...
I was trying to remove the  system monitor to save resources..and I killed that process...

However, for the future, How do I reinstall  ubuntu without starting from scratch?

Because it is been going real slow lately..

---

