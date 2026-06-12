---
title: "Can you specify an Ubuntu release with add-apt-repository?"
date: 2010-01-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-01-02
Or does it stupidly assume the version I run is the same as the highest version offered by the PPA?

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/502454](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/502454)

---

### Post by Eclipse. on 2010-01-02
> **Starks said:**
> Or does it stupidly assume the version I run is the same as the highest version offered by the PPA?

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/502454](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/502454)

I commented on launchpad, seems like work with no real gain to be honest.

---

### Post by ronacc on 2010-01-02
I believe when adding repositories apt tries to maintain consistancy with the installed version to be certain that apps you install will actualy work and not muck up the system . It is not really meant for those of us who cross install and otherwise torture our installs .:P You can always edit your /etc/apt/sources.list to get the version you want and then sit back and watch your box meltdown . :lolflag:

---

### Post by Starks on 2010-01-02
Yeah, but I want a single, powerful terminal command. Fiddling with files is time consuming.

---

### Post by last1 on 2010-01-02
Seems like a decent idea to me.

---

### Post by oldsoundguy on 2010-01-02
If you are not attempting to run updates from  other than the build you are using:

[http://blog.ubuntu-tweak.com/downloads](http://blog.ubuntu-tweak.com/downloads)

pick your build and install.  Saves line after line of entry into the sources list.

---

### Post by Starks on 2010-01-02
> **oldsoundguy said:**
> If you are not attempting to run updates from  other than the build you are using:

[http://blog.ubuntu-tweak.com/downloads](http://blog.ubuntu-tweak.com/downloads)

pick your build and install.  Saves line after line of entry into the sources list.
You have to spoof your lsb_release and other files to read as "karmic" to get those functions of Ubuntu-Tweak to work with Lucid.

---

### Post by jerrylamos on 2010-01-04
Simple reason for trying to back level on releases:

Alpha's & Beta's break!  Apt-get update, dist-upgrade crash, again and again, need to back level before the update.

What I do now is try to re-install a previous daily build if I happen to have one around.

Jerry

---

### Post by slakkie on 2010-01-04
> **Starks said:**
> Yeah, but I want a single, powerful terminal command. Fiddling with files is time consuming.

```

echo "deb http://ppa.launchpad.net/wesleys/ppa jaunty main" | sudo tee -a /etc/apt/sources.list

```

One single line.

---

### Post by Starks on 2010-01-04
> **slakkie said:**
> ```

echo "deb [http://ppa.launchpad.net/wesleys/ppa](http://ppa.launchpad.net/wesleys/ppa) jaunty main" | sudo tee -a /etc/apt/sources.list

```One single line.
Doesn't grab GPG keys and isn't short enough or easy to remember. It's also not technically a single command if you use pipes.

This is what I want:
```
sudo add-apt-repository ppa:ubuntu-boot/staging --distro=karmic
```

---

### Post by philinux on 2010-01-04
> **Starks said:**
> Doesn't grab GPG keys and isn't short enough or easy to remember. It's also not technically a single command if you use pipes.

This is what I want:
```
sudo add-apt-repository ppa:ubuntu-boot/staging --distro=karmic
```

Somebody with scripting skills should be able to modify the script to do what you need to create a custom one.

```
cat /usr/bin/add-apt-repository
```

---

### Post by Starks on 2010-01-04
Ooh. It's Python! I just took a class for basic Python. Maybe I could do that and submit a patch.

(No, I'm not committing to fixing the bug.)

---

