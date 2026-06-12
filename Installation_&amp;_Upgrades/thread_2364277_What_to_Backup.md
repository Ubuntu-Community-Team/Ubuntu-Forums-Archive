---
title: "What to Backup"
date: 2017-06-21
forum: Installation &amp; Upgrades
---

### Post by jek1 on 2017-06-21
I use Ubuntu 14.04 LTS. I recently had a system crash and had to reinstall the OS. I used rsync to backup my home-folder and could recover all my data. However, it cost me a pretty penny in downloads (and time) to restore all the software again to what it was before the crash. Now my question is, what other system folders can I safely backup and restore (using rsync) to minimise all this costly downloads, should something like this happen again?

---

### Post by TheFu on 2017-06-21
If you don't want to download anything, then you want a bit-for-bit image backup.

I find that wasteful, since versioned backups are critical to system security.  Having 1 backup addresses about 70% of backup needs, but versioned backups handle 100%.

Lots of posts here cover what needs to be backed up and other techniques.  I don't backup program files. I do backup program lists, program settings, and system settings.  Of course, I get all the data - /home, /var/www, /var/lib/ and /usr/local/

Generally, to restore a system to nearly identical working condition takes 30-45 min.

---

### Post by jek1 on 2017-06-21
Thanks TheFu. Is it possible to post some links to those posts you are referring to? I did do a search for “what to backup”, but I just got quite a lot of unrelated posts.

---

### Post by SeijiSensei on 2017-06-21
First, you can create a list of installed software with the command "dpkg --set-selections".  It will create a inventory list that you can read back onto a new installation and update the software to match what was there before.

The most critical directory to back up other than /home is /etc.  It's where many programs store their settings.  I also back up /var and /usr/local where I put custom scripts and programs I write.

Do you have serious limits on bandwidth or an expensive Internet connection?  I'm guessing that must be true since you claim it cost you a "pretty penny" to download the software.  Most modern Linux distributions assume a decent level of Internet connectivity to remain current.  For someone like me with an all-you-can-eat type of connection, these issues never arise.  Do you have any alternatives?

---

### Post by TheFu on 2017-06-21
**dpkg --get-selections** doesn't work the way it used to anymore.  Discovered this a few weeks ago as I reloaded 16.04 on a laptop (wanted a 50% encrypted setup) so the other half could boot other OSes.  Seems there isn't any method to differentiate between *all packages manually loaded* and those loaded through dependencies anymore.  **apt-mark** doesn't help either.

In theory, **apt-mark showmanual** should work, but it doesn't, not always.
A number of answers on askUbuntu.com show different solutions. My testing showed font- packages as manually installed, which never happened.
These didn't work perfectly, but close:
```
# aptitude search '~i !~M' -F '%p' --disable-columns | sort -u > currentlyinstalled.txt
# comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u)
# comm -23 <(aptitude search '~i !~M' -F '%p' | sed "s/ *$//" | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u)

```
These are separate commands. Some refs:
[https://askubuntu.com/questions/17823/how-to-list-all-installed-packages](https://askubuntu.com/questions/17823/how-to-list-all-installed-packages)
[https://askubuntu.com/questions/2389/generating-list-of-manually-installed-packages-and-querying-individual-packages](https://askubuntu.com/questions/2389/generating-list-of-manually-installed-packages-and-querying-individual-packages)

There is a GUI backup tool for end users that captures themes, settings, and their HOME. Sorry, I don't remember the name. Someone else might remember it. Since it is a GUI, it doesn't work on servers.

---

### Post by #&amp;thj^% on 2017-06-21
Not sure if this is the one you are referring to...but worth a mention FWIW: [http://www.teejeetech.in/2016/04/upgrade-to-ubuntu-1604-with-aptik.htmlv](http://www.teejeetech.in/2016/04/upgrade-to-ubuntu-1604-with-aptik.htmlv)
Great advice shown in your above post though. :)

---

### Post by jek1 on 2017-06-21
> **SeijiSensei said:**
> Most modern Linux distributions assume a decent level of Internet connectivity to remain current.

That is actually a very unfair assumption!  Not everybody in the world have free internet.

Anyway, thanks for the help guys. I will certainly use some of your suggestions and hope it will save me some costly downloads if I ever have to reinstall Ubuntu again.

---

### Post by deadflowr on 2017-06-21
Depending on the update method used you can do a poor man's package backup.
The packages for Ubuntu's updates are contained in the folder /var/cache/apt/archives.
so simply copying the packages listed in here to the new location will bring them in there.
From there you can run a simple sudo apt-get update and sudo apt-get dist-upgrade to update them.
In use with the dpkg --get(set)-selections tomfoolery you can re-install all the packages from one to another with little trouble.

Back to why it depends is that if you use the cli apt-get or Ubuntu's builtin gui Software Updater, they hold those packages indefinitely.

But, if you update or install using the newer apt command ; ala sudo apt install some-package, then that command only holds packages until the package is successfully installed.
When the package install succeeds those packages get purged.

It also depends if whether you've run apt-get clean, as that also purges the archives, completely.
(sudo apt-get autoclean purges packages too, but only older obsolete packages, it'll keep the latest installable packages for let's say the newest kernel version or newest Firefox version.)

Note also that this only works moving from sand to the same version of Ubuntu, of course.
(you can't decide to use this method if trying to move from something like Ubuntu 14.04 to 16.04, as none of the listed archived packages would even be known to 16.04.
and vice versa)

Again, a poor man's method of moving the packages from one to another.
And done right, will cut down what you would need to download of the net drastically.

Hope that makes sense.

---

### Post by SeijiSensei on 2017-06-21
> **jek1 said:**
> That is actually a very unfair assumption!  Not everybody in the world have free internet.
Windows isn't really any different these days.  Microsoft rolls out updates all the time and expects you to download and install them.

---

### Post by TheFu on 2017-06-21
> **jek1 said:**
> That is actually a very unfair assumption!  Not everybody in the world have free internet.

I've never met anyone with free internet at home in all my travels.

---

### Post by jek1 on 2017-06-22
> **SeijiSensei said:**
> Windows isn't really any different these days.  Microsoft rolls out updates all the time and expects you to download and install them.

So what then makes Ubuntu any better than Windows??? I Changed from Windows to Ubuntu because I thought that it would be more user-minded. Now it seems the Ubuntu community is just another flock of sheep following the great shepherd.

> **TheFu said:**
> I've never met anyone with free internet at home in all my travels.

Good for you TheFu. I can’t even afford to travel any more, not even on the internet.

And thanks again to everyone for all the useful information here.

---

