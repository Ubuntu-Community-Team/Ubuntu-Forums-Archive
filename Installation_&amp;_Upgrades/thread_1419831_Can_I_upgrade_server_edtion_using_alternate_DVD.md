---
title: "Can I upgrade server edtion using alternate DVD?"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by fade2gray on 2010-03-02
The guide gives me the impression that the alternate DVD is only suitable for upgrading the desktop edition.

> Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.

    * If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

      ```
sudo mount -o loop ~/**Dektsop**/ubuntu-8.10-alternate-i386.iso /media/cdrom0
```

---

### Post by Sef on 2010-03-02
/Desktop is the location of where the file is located.

---

### Post by fade2gray on 2010-03-02
> **Sef said:**
> /Desktop is the location of where the file is located.

Yes, I appreciate that, but...

"Network Upgrade for Kubuntu **Desktops** (Recommended)"... no abiguity.

"Network Upgrade for Ubuntu **Servers** (Recommended)"... no abiguity.

"Upgrading Using the Alternate CD/DVD"... followed with a reference to a **Desktop** directory made me feel a little unsure as I wouldn't expect to find a desktop directory in a server installation, hence the original question, "Can I upgrade server edtion using alternate DVD?".

---

### Post by wojox on 2010-03-02
So if it's in your /home/<username>/ directory just use:

```
sudo mount -o loop ~/ubuntu-8.10-alternate-i386.iso /media/cdrom0
```

What version are you upgrading from ?

---

### Post by fade2gray on 2010-03-02
> **wojox said:**
> What version are you upgrading from ?

8.04 to 9.10 with the appropriate steps in between.

---

### Post by wojox on 2010-03-02
Cant you just upgrade like this:

```
sudo apt-get install update-manager-core
```

```
sudo do-release-upgrade
```

That's how I've upgraded my servers.

---

### Post by fade2gray on 2010-03-03
> **wojox said:**
> Cant you just upgrade like this:

```
sudo apt-get install update-manager-core
```

```
sudo do-release-upgrade
```

That's how I've upgraded my servers.
I agree that seems to be the easy option, but having read [this]("http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server") 'how to'...

> Fetching and installing the upgrade can take [COLOR="Red"]several hours[/COLOR].
Once the download has finished, the process cannot be cancelled.

and that's just 8.04 to 8.10, I thought it might be me more efficient and less time consuming to upgrade via torrent images.

---

