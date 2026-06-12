---
title: "Add repository without giving command of my computer to some random server"
date: 2013-08-09
forum: Installation &amp; Upgrades
---

### Post by aerojockey on 2013-08-09
So basically I have a software issue where I need to install something from a thrid-party repository to be able to do a simple computing function because the baseline software has a bug.  Oh well, it happens.  Back in the day, I would add a line to my /etc/apt.sources, and maybe type in a command to update repository credentials.  It was very simple.

Now I have to use this craptastic command line tool called add-apt-repository, and I see that to run it, I have to install a package called python-software-properties, which in turn insists that I install a package called unattended-upgrades, which "helpfully" installs "upgraded" software without asking me.

Well, geez.  If I wanted that drama I would have just stayed with Windows.  And unlike Ubuntu, at least Windows learned its lesson and lets you shut this off.

Well, my question is, how can I add a ppa repository without having to install unattended-upgrades?

---

### Post by SweetAurora on 2013-08-09
Unattended upgrades is nothing more than a feature of Debian that allows upgrading safe components of the OS without the need of the Users Password. By default, it isn't enabled and requires editing apt configs to enable it. So don't worry. Also, there are no "Random servers" in Ubunu. All packages upload to Ubuntu's archives are mirrored across many certified Ubuntu Repository Servers. So adding that line in apt will give you a trusted server always. By default it's Canonical servers, but you can choose from a list of servers as to where you want your packages to come from.

At least that's my beliefs of the system.

---

### Post by Cheesemill on 2013-08-10
You can still just add the line for the PPA to your sources.list file (this is all the add-apt-repository command does anyway).

Visit the PPA's overview page in Launchpad. Look for the heading that reads Adding this PPA to your system and click the Technical details about this PPA link.

Use the Display sources.list entries drop-down box to select the version of Ubuntu you're using, you'll see that the text-box directly below reads something like this:

```
deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main
```

Copy those lines.

Open a terminal and type:

gksudo gedit /etc/apt/sources.list

This will open a text editor containing the list of archives that your system is currently using. Scroll to the bottom of the file and paste the lines you copied in the step above.

Save the file and exit the text editor.

Back on the PPA's overview page, look for the Signing key heading. You'll see something like:

1024R/72D340A3 (What is this?)

Copy the portion after the slash but not including the help link; e.g. just 72D340A3. Now you need to add that key to your system so Ubuntu can verify the packages from the PPA. In your terminal, enter:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
```

(Replace 72D340A3 with whatever you copied earlier).

This will now pull down the PPA's key and add it to your system.

Now, as a one-off, you should tell your system to pull down the latest list of software from each archive it knows about, including the PPA you just added:
```
sudo apt-get update
```

Now you're ready to start installing software from the PPA!


As mentioned above though having the unattended-upgrades package installed isn't an issue. It will only automatically update your system if you enable it. The only reason the method I've outlined above isn't used much any more is that python-software-properties is already installed by default on all current desktop versions of Ubuntu.

---

