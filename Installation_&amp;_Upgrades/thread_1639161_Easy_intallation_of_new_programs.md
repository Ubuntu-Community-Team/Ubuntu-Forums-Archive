---
title: "Easy intallation of new programs"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by BlueTemplar on 2010-12-06
I'd like to update /etc/apt/sources.list with all the packages available on packages.debian.org and packages.ubuntu.com without apt-get, aptitude, and synaptic then trashing my system by trying to update all the obsolete packages. (I'm stuck with 8.04)

I only want to update the packages / install new ones with their dependencies as I request them. How do I do that?

---

### Post by karthick87 on 2010-12-06
Welcome to ubuntuforums :)

Why dont you go with apt-get and synaptic?

---

### Post by snowpine on 2010-12-06
Welcome to the forums!

First, please don't break your system by trying to mix Ubuntu and Debian software sources. They are separate distros and are not 100% binary compatible.

If I understand your question correctly, all you need to do to keep your system up-to-date with the latest bug fixes and security patches is to run the Update Manager periodically, or use the terminal commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If you have questions about a specific app (or apps) I will try my best to help.

---

### Post by BlueTemplar on 2010-12-06
The problem is that most of the programs I want to install are not listed in my sources.list ...

And I am already up to date (for 8.04...)

---

### Post by snowpine on 2010-12-06
> **BlueTemplar said:**
> The problem is that most of the programs I want to install are not listed in my sources.list ...

And I am already up to date (for 8.04...)

Individual applications do not appear listed in /etc/apt/sources.list. That is not the purpose of the file.

Try using the Add/Remove Software application, the Synaptic Package Manager, or terminal commands (such as "sudo apt-get install firefox") to install your application.

If you want additional help, you need to tell us which specific app(s) you are having trouble installing.

---

### Post by madjr on 2010-12-06
have you tried upgrading using an usb stick to a more recent version of ubuntu ?

---

### Post by karthick87 on 2010-12-06
If you want to install additional packages you wanna add their ppa to repositories.

---

### Post by BlueTemplar on 2010-12-06
What I meant to say that the programs I wanted to install were not in the repositories to which my sources.list is pointing.

It's not that i'm having trouble installing so much that is cumbersome to download manually the programs and their dependencies then install them while it could be ndone automatically with a single command line...
For instance flvstreamer was not in the list of my programs.

I'm stuck with 8.04 because of easy peasy.

What's a ppa?

---

### Post by karthick87 on 2010-12-06
PPA - Personal Package Archive it can provide alternate software not normally available in the offical Ubuntu repositories.

---

### Post by snowpine on 2010-12-06
flvstreamer is in the repositories for Karmic, Lucid, or Maverick and can be easily installed with 2 clicks through the Software Center. I understand your frustration, but please understand that you are 4 releases and over 2 years behind the curve; you could easily resolve your frustration by using a current Ubuntu release.

Anyways, you can get flvstreamer here: [http://www.nongnu.org/flvstreamer/](http://www.nongnu.org/flvstreamer/)

If there are any other apps you're looking for, let me know and I'll help you Google them. ;)

---

### Post by karthick87 on 2010-12-06
```
sudo apt-get install flvstreamer
```

---

### Post by BlueTemplar on 2010-12-06
[http://launchpad.net](http://launchpad.net) doesn't seem to be working right now, I'll try later...

Yes, but [http://olaf.10.free.fr/urecorder/urecorder_0.9-1_all.deb](http://olaf.10.free.fr/urecorder/urecorder_0.9-1_all.deb) has several dependencies for instance...

Yes, maybe I should just drop easy peasy... I have an eeepc 901, do you know any good release that would go well with that?

Thank you, but I don't have too many problems finding programs usually, though if you know a good one for HTTP tunneling, or to connect to internet with a 3G usb modem, let me know. ;)

---

### Post by snowpine on 2010-12-06
> **BlueTemplar said:**
> Yes, but [http://olaf.10.free.fr/urecorder/urecorder_0.9-1_all.deb](http://olaf.10.free.fr/urecorder/urecorder_0.9-1_all.deb) has several dependencies for instance...

Dependencies are a normal part of running a Debian-based distro like Ubuntu or Easy Peasy. In most cases, we install an application from the repositories, in which case the dependencies are automatically installed from the same repositories. If you are installing a .deb that is not designed for your specific release, then yes, unfortunately you may need to manually satisfy these dependencies (and your system may become less stable).

> **BlueTemplar said:**
> Yes, maybe I should just drop easy peasy... I have an eeepc 901, do you know any good release that would go well with that?

Ubuntu is a good place to start; that would be my suggestion.

---

### Post by madjr on 2010-12-06
> **BlueTemplar said:**
> 

Yes, maybe I should just drop easy peasy... I have an eeepc 901, do you know any good release that would go well with that?



ubuntu or the latest easy peasy

[http://www.geteasypeasy.com/easypeasy-1-6-released/](http://www.geteasypeasy.com/easypeasy-1-6-released/)

---

### Post by BlueTemplar on 2010-12-06
EP 1.5 is still only ubuntu 9.4, and EP 1.6 seems to be bugged... is the Ubuntu Netbook Edition any good?

---

### Post by snowpine on 2010-12-06
> **BlueTemplar said:**
> is the Ubuntu Netbook Edition any good?

Many users on these forums think so. Best advice is to burn a Live CD/USB and take it for a test drive, form your own opinion. :)

---

### Post by madjr on 2010-12-07
use netbook remix 10.04 is faster.

---

