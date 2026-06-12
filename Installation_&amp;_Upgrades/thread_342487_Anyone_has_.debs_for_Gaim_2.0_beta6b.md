---
title: "Anyone has .debs for Gaim 2.0 beta6b?"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by gabrielsaldana on 2007-01-20
Now that Gaim 2.0 beta 6b is out, does anyone know how to build and install it? Or has already packaged some .deb files to install?

There are a few bugs on beta 5 that I hope are fixed on this update.

---

### Post by joshier on 2007-01-20
Same here...

---

### Post by Pobega on 2007-01-20
[http://downloads.sourceforge.net/gaim/gaim-2.0.0beta6.tar.gz?modtime=1169170207&big_mirror=1](http://downloads.sourceforge.net/gaim/gaim-2.0.0beta6.tar.gz?modtime=1169170207&big_mirror=1)

Assuming you downloaded to your /home/$USER directory:
> tar xvvf gaim-2.0.0beta6.tar.gz
cd gaim-2.0.0beta6
./configure
make
sudo (checkinstall) make install

Checkinstall is optional, depending on if you use it or not (Recommended)

---

### Post by vr04 on 2007-01-20
I made a quick bash script which will allow you to compile gaim2.0beta6 and the guifications plugin.

[COLOR="Red"]Before you run the script, you should remove older versions of Gaim[/COLOR]

Open a terminal, and type
```
wget http://web.tampabay.rr.com/vr/ubuntu/installgaim
```

Now, make the script executable
```
chmod +x installgaim
```

Finally, run the script
```
./installgaim
```

You will have to type in your password, and the script will do the rest.

Be advised that it may take a while to build.

Also, if Gaim doesn't show up in Applications > Internet after you've built it, refresh your gnome-panel by doing
```
killall gnome-panel
```

---

### Post by Pobega on 2007-01-20
A script would work, but I personally think the only way to learn is to try to do things yourself; Being able to do ./configure and make is probably one of the more important things one has to learn when using Linux. But, good work none the less.

---

### Post by vhscampos on 2007-01-20
> **Pobega said:**
> A script would work, but I personally think the only way to learn is to try to do things yourself; Being able to do ./configure and make is probably one of the more important things one has to learn when using Linux. But, good work none the less.

Agreed.

Specifically in case of Gaim, checkinstall goes better than make install

---

### Post by rgeide on 2007-01-20
Have you tried downloading the .rpm file then:
```
sudo alien -c *Insert rpm file name here.*
```

That will generate your deb file with scripts.   Then you can just double-click to install.

You can get alien via:
```
sudo apt-get install alien
```

---

### Post by Pobega on 2007-01-20
And if you use the .deb you can uninstall the package using > dpkg -r gaimI'm not sure if *gaim* needs the version number following it, but I doubt it.

Actually, same goes for checkinstall too.

---

### Post by vhscampos on 2007-01-20
I've tried to 'alien' the rpm, but it didn't work well.

Here's the resulting deb from checkinstall:
[http://rapidshare.com/files/12580224/gaim_2.0.0beta6-1_i386.deb.html]("http://rapidshare.com/files/12580224/gaim_2.0.0beta6-1_i386.deb.html")

> **Pobega said:**
> And if you use the .deb you can uninstall the package using I'm not sure if *gaim* needs the version number following it, but I doubt it.

No, it doesn't.

---

### Post by danhm on 2007-01-20
Has anyone found a change log? I'd like to know what I'm getting before I upgrade from beta 5.

---

### Post by Pobega on 2007-01-20
> **danhm said:**
> Has anyone found a change log? I'd like to know what I'm getting before I upgrade from beta 5.

Nothing in the changelog seems to have changed, so I'm not sure what the difference between beta5 and beta6 is.

---

### Post by niekko on 2007-01-21
The release notes are at [[COLOR="Blue"]http://sourceforge.net/project/shownotes.php?release_id=479631&group_id=235[/COLOR]]("http://sourceforge.net/project/shownotes.php?release_id=479631&group_id=235").

---

### Post by danhm on 2007-01-21
Well, I upgraded. However, the Update Manager thinks that beta5 is a more recent version; what should I have told checkinstall to make the version number for beta6?

Right now Update Manager wants me to go from "2.0.0beta6-1" to "1:2.0.0+beta5-0ubuntu2".

---

### Post by Pobega on 2007-01-21
> sudo nano /etc/apt/preferences
In the preferences file copy and paste this:> Package: gaim
Pin: version 2.0.0*
Pin-Priority: 1001Now to exit nano and save your changes hit Ctrl+X, then Y. The /etc/apt/preferences file tells apt to not update the program. Just so you know, it won't prompt you to update Gaim **ever**, but Gaim itself in it's preferences has a choice to check for updates. I advise you use that instead of aptitude.

---

### Post by danhm on 2007-01-21
Thanks!

---

### Post by cendant on 2007-01-21
**Gaim 2 beta 6**

[http://rapidshare.com/files/12757151/gaim_1_3a2.0.0_beta6-0ubuntu4_i386.deb]("http://rapidshare.com/files/12757151/gaim_1_3a2.0.0_beta6-0ubuntu4_i386.deb")

**Gaim 2 beta 6 (data)**

[http://rapidshare.com/files/12758495/gaim-data_1_3a2.0.0_beta6-0ubuntu4_all.deb]("http://rapidshare.com/files/12758495/gaim-data_1_3a2.0.0_beta6-0ubuntu4_all.deb")

---

### Post by i.be.doh32 on 2007-01-21
I've installed via checkinstall for gaim beta5 and beta6, but it doesn't seem to create a .deb file for gaim-data.  Am I doing something wrong or is there more that I need to do or what?

Thanks in advance.

-----

Also, when i was able to successfully install the above gaim-data package alongside my own compiled gaim package (via instructions on [compile gaim]("https://help.ubuntu.com/community/CompileGaim?highlight=%28gaim%29#head-97ab73ee35145a3fd8ea1259c8446f609ed20973") page in the community docs), there is no sound.  This also happened before whenever I would build gaim on my own (via said instructions).  I am curious if the gaim-data package is necessary at all?  It might also be that the above gaim-data package is for Ubuntu 6.10, when I am using 6.06.

---

### Post by libos on 2007-01-22
> **Pobega said:**
> In the preferences file copy and paste this:Now to exit nano and save your changes hit Ctrl+X, then Y. The /etc/apt/preferences file tells apt to not update the program. Just so you know, it won't prompt you to update Gaim **ever**, but Gaim itself in it's preferences has a choice to check for updates. I advise you use that instead of aptitude.

Or you can use the "Lock Version" feature in Synaptic Package Manager.

---

### Post by Pobega on 2007-01-22
> **libos said:**
> Or you can use the "Lock Version" feature in Synaptic Package Manager.

That has never worked for me, I just prefer to use /etc/apt/preferences. It makes more sense to me, and it's easy to change.

---

### Post by i.be.doh32 on 2007-01-22
Does anybody know how to compile gaim-data for Dapper?  The packages above posted by cedant don't work for me.

---

### Post by Pobega on 2007-01-22
> **i.be.doh32 said:**
> Does anybody know how to compile gaim-data for Dapper?  The packages above posted by cedant don't work for me.

Don't use the .debs, just install the package from source. It's much easier and works better that way.

---

### Post by i.be.doh32 on 2007-01-22
Ok, I just re-built it from source, and I figured out what the sound issue was.  Under tools>preferences>sound tab, the method was set to console beep instead of automatic.  So its all fixed now.

---

### Post by magomago on 2007-01-22
Well I upgraded using some repo that I got for beta5 (apparantly they updated for beta6, thanks whoever is hosting it :))


But does anyone know if file transfers don't keep crashing (aim specifically?)  I can't test it out till later, but it happens often, yet erraticaly

Does MSN file transfer also still suck balls?  

And one last thing that I never figured out - can we have our own custom icons in MSN?  Clearly we can atleast see them, but its another on whether or not we can use it ;)

---

### Post by foureight84 on 2007-01-22
> **danhm said:**
> Well, I upgraded. However, the Update Manager thinks that beta5 is a more recent version; what should I have told checkinstall to make the version number for beta6?

Right now Update Manager wants me to go from "2.0.0beta6-1" to "1:2.0.0+beta5-0ubuntu2".

when you do make the package with checkinstall, change the version to "1:2.0.0+beta6-1ubuntu9-1" i had the same version with beta5 when it first came out.

---

### Post by Gathalimay on 2007-01-22
Do I need to add in a new repository for gaim or something? I'm on beta3 and the add/remove thing still says 2.3. The install keeps failing. It won't let me get past ./configure. Says:

checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
gathalimay@gathalimay-desktop:~/Desktop/gaim-2.0.0beta6$ sudo make
make: *** No targets specified and no makefile found.  Stop.


I haven't removed the old gaim, because it says It's part of the system (nautilus depends on it). Last time I tried something like that it nuked my entire linux box and I had to reinstall. Maybe I'm just paranoid about removing it since that happened. Is it ok to remove (I have to do it via synaptic package manager right?)?

---

### Post by Pobega on 2007-01-23
I'm pretty sure Gaim is just a metadependency of Nautilus, the previous version of Gaim should be safe to remove.

---

### Post by foureight84 on 2007-01-29
if you have problem running ./configure, then try to install the gaim dependencies first

sudo apt-get build-dep gaim

---

### Post by maynoth on 2007-01-29
deb  [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse

add that to your sources.list  always has the latest gaim betas compiled for edgy

---

### Post by th3gh05t on 2007-01-30
> **vr04 said:**
> I made a quick bash script which will allow you to compile gaim2.0beta6 and the guifications plugin.

[COLOR="Red"]Before you run the script, you should remove older versions of Gaim[/COLOR]

Open a terminal, and type
```
wget http://web.tampabay.rr.com/vr/ubuntu/installgaim
```

Now, make the script executable
```
chmod +x installgaim
```

Finally, run the script
```
./installgaim
```

You will have to type in your password, and the script will do the rest.

Be advised that it may take a while to build.

Also, if Gaim doesn't show up in Applications > Internet after you've built it, refresh your gnome-panel by doing
```
killall gnome-panel
```

Hi,

I ran your script, and it ended with this:

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
make: *** No targets specified and no makefile found.  Stop.
sudo: checkinstall: command not found


Did it successfully install?

Help please...

---

### Post by th3gh05t on 2007-01-30
Hi,

I want to go back to version 1.5.

How do I do that?

File transfer doesn't work with version 2.0.

How do I go back to version 1.5?

Also, I get this error in Apt-get

E: The package gaim needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by Hanzerik on 2007-01-30
Another option is not to install it system wide.

mkdir ~/MyApps
mkdir ~/MyApps/Gaim
tar -xzvf whatever-app.tar.gz
cd whatever-app
./configure --prefix=$HOME/MyApps/Gaim
make
make install

./MyApps/Gaim/bin/gaim

This way if you don't like it just remove the MyApps/Gaim directory.

---

### Post by vr04 on 2007-01-31
> **th3gh05t said:**
> Hi,

I ran your script, and it ended with this:

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
make: *** No targets specified and no makefile found.  Stop.
sudo: checkinstall: command not found


Did it successfully install?

Help please...

ghost,

my script installs intltool and checkinstall, which are both required to install the way i set it up. the reason the script failed is most likely because you don't have universe/multiverse repos enabled. if you dig in the forums or over at [http://wiki.ubuntu.com](http://wiki.ubuntu.com) you can find out how to add those extra repos to your system. sorry i can't be of more help right now, i'm tired as hell!

---

### Post by Zer0Nin3r on 2007-02-01
> **magomago said:**
> Well I upgraded using some repo that I got for beta5 (apparantly they updated for beta6, thanks whoever is hosting it :))


But does anyone know if file transfers don't keep crashing (aim specifically?)  I can't test it out till later, but it happens often, yet erraticaly

Does MSN file transfer also still suck balls?  

And one last thing that I never figured out - can we have our own custom icons in MSN?  Clearly we can atleast see them, but its another on whether or not we can use it ;)

That's kind of scary "*..using some repo...*."  I guess that's a security risk that one is willing to take.

Anyway, I haven't upgraded, and I'm using the version Edgy came with (beta 3) and I"ll get crashing problems when direct connecting or transferring files.  No bug report is generated though...food for thought.

---

### Post by routerstu on 2007-02-02
use the debuntu repo for the latest gaim.  works great!!!!

---

### Post by maynoth on 2007-02-04
> **routerstu said:**
> use the debuntu repo for the latest gaim.  works great!!!!

Ya.. I know.. who cares about compiling crud from source... 
I wish there was a repo for OOo firefox, n thunderbird too

---

### Post by Flavian on 2007-02-08
Hi guys! Anyone knows a solution?
I tried to compile the newest gaim via source and ./configure goes well till it reaches the last point.
And there I get dependency issues. I don't know where they are coming from!
And I don't know how to fix them. tracking them down and installing every package by hand slowly ends up in a corner :(

That's what I get
> 
checking for IceConnectionNumber in -lICE... yes
checking for GTK... no
configure: error:

You must have the GTK+ 2.0 development headers installed to compile Gaim's
GTK+ interface.  If you only want to build the console interface then
specify --disable-gtkui when running configure.


When I try to install the GTK dev headers, I get all those dependency errors! DANG IT!
Please help me :(

---

### Post by vr04 on 2007-02-10
Flavian,

Do you have libgtk2.0-dev installed?

---

### Post by Shed on 2007-02-13
> **maynoth said:**
> deb  [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse

add that to your sources.list  always has the latest gaim betas compiled for edgy

Thank you!

---

### Post by jfca283 on 2007-04-24
i can't apply any theme with gaim
i used the script to get beta 6
who could make it?
install and apply a theme?

---

