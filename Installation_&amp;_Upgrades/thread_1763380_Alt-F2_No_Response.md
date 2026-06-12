---
title: "Alt-F2 No Response"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by Epsymp on 2011-05-20
I upgraded to Firefox 4.0.1 (which took a ton of effort, though it'd take five seconds if I had to do it again).

Today I fixed the link in the toolbar to open up the new version instead of the old version, by replacing the Firefox folder in the usr/lib folder, and specifying the location and name in the properties of the icon.

I realized that somehow I messed up something, and Alt-F2: "firefox" no longer runs firefox. Any ideas about how Alt-F2 works? I'm guessing it's a /bin, but experiments injecting Firefox into /bin's hasn't worked.

Thanks

---

### Post by ajgreeny on 2011-05-20
Which version of xubuntu, and how did you install FF4?  Perhaps the executable is in /opt and not /usr/bin, as happens when you install some things alongside a currrent version of the same.  I am sure FF4 is already in xubuntu 11.04, so it is obviously a previous version, but which one?

---

### Post by Epsymp on 2011-05-20
Hi AJ,

I'm on an old one, 9.04, because it's the only one my wireless card works with.

I don't think I actually "installed" firefox, just downloaded and extracted the .tar to /opt and /usr/lib.

Thanks

---

### Post by ajgreeny on 2011-05-20
The problem is that the executable is either in /opt or /usr/lib, neither of which are normally in your $PATH (you can find what folders are in the PATH with command ```
echo $PATH
``` in terminal, and it is only executables in those folders that are run from the executable's file name in terminal.  As you still have the distro's own version of FF installed, that is what runs when you use that command.

To use a launcher you will need to make a new launcher with the full pathway to the executable, eg **/opt/firefox-4/firefox**, or something similar, but I will have to let you find it yourself as I have not installed FF4.

---

### Post by Epsymp on 2011-05-21
Thanks again.
/opt/firefox/firefox does the trick.

I ran echo $PATH and got the following:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

So I'm guessing there has to be an executable file in one of those folders for the command to work, and I just have to find where the old firefox executable is and replace it?

---

### Post by ajgreeny on 2011-05-21
> **Epsymp said:**
> Thanks again.
/opt/firefox/firefox does the trick.

I ran echo $PATH and got the following:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

So I'm guessing there has to be an executable file in one of those folders for the command to work, and I just have to find where the old firefox executable is and replace it?
Correct, though to keep both available, you can make your new launcher called FF4 point to /opt/firefox/firefox and keep the old launcher as it is, then you can launch either FF as you wish.

Just watch out for any changes in the profile that FF4 may make, stopping FF3.6.x doing what you expect, eg with some add-ons which may not yet work in FF4 buit do in FF3.6.x.

---

### Post by Epsymp on 2011-05-21
Thanks again.
So a command needs to have a path that points to the application folder.

I'm not sure how to point it.
Is it something like:
ln -a /usr/firefox/firefox /usr/local/bin
(or is it the other way around? ln -a /usr/local/bin /usr/firefox/firefox)

then "firefox" in the command line would be able to run the firefox application, since "/usr/local/bin" is one of the folders listed by "echo $PATH?"

---

### Post by Epsymp on 2011-05-21
OK.
I messed around a little.

I did sudo ln -s /opt/firefox /usr/bin/firefox

If I run "firefox" command it says it can't run the child process (permission denied), which makes sense since it's a root folder.

If I try in terminal it says there's no firefox installed. If I do /usr/bin/firefox/firefox it runs. So the link is working.

So I try to do ln -s /usr/firefox/fire firefox, try again to run it...same permission problem.

It's not a big deal, I'd just appreciate if someone could help me figure out exactly how this thing is working.

---

### Post by ajgreeny on 2011-05-21
Can we start again from the beginning; do you want to replace Firefox 3.6.x or do you want to have both FF3.6.x and FF4 available to run?  If you want both, do as I said and make a new launcher for FF4 which you can put on the desktop or in the menu whichever you want, but in the command box of that launcher type **/opt/firefox/firefox** not just **firefox**, which as you now know will launch FF3.6.x.

If you did not want to keep FF3.6.x you could always remove it using synaptic, but I don't know if the presence of FF4 will upset that activity.  The linking you are trying to do can work, but is a bit more difficult to achieve, I have never tried it, but I think you will need to do it as root, using sudo for that command.

---

### Post by Epsymp on 2011-05-21
I don't want to keep firefox 3.6.x. It uninstalled just fine.

What I still don't understand is what's required for any application to open in the run program command line. I thought it was just that the executable be in any of the folders listed for $PATH, but I think that's wrong...or if it's true, why don't I need sudo for those as well.

Sorry to waste your time, it's not totally necessary, I can type out /opt/firefox/firefox just fine, I'm mostly just curious...

---

### Post by ajgreeny on 2011-05-22
I think I am now out of my depth, and will have to step away from this for fear of making things worse for you.  If ever I have used a firefox downloaded tar.gz for an application, I have left the extracted archive in /home, not put it in /opt, so I have simply made launchers in my menu pointing to that.

I hope you get it sorted to your satisfaction, but altarnatively add the ppa with FF4 so you can install it with synaptic or apt-get and then everything will work just as if it were still FF3.6.x.
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

---

