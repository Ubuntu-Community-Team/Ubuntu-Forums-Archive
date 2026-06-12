---
title: "Frozen Upgrade (Hardy to Lucid)"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by Stieffers on 2010-09-28
I attempted to upgrade my computer from Hardy to Lucid today and unfortunately the system froze when the upgrade GUI read "Installing updates."  The system still boots, but directly into terminal.  XFCE no longer loads.

I've tried updating and fixing updates, but I can't connect to my network (which I can't control, public network of sorts) but there's a WPA2 key, so iwconfig is out of the question.  Any help would be much appreciated.

**Edit**:  So I solved the problem.  I'll list the steps required to fix it incase anyone else runs into the issue.

You'll need a few things.  since I don't have a CD-Rom on the computer in question I had to use a USB key, but either will do.  Get a copy of Ubuntu and burn the image to a disk, or write it to a USB key.  Boot into Ubuntu using the live disk / USB.  Open up terminal and firstly mount the drive in question.

```
sudo mkdir /mnt/repair
sudo mount /dev/[drive number and letter] /mnt/repair
```

Use the drive you need.  Mine was "sda1."  Next you'll need to change you working root directory to your new drive.

```
sudo chroot /mnt/repair su
```

This command will but you into an operational root of you mounted drive.  You will now be able to run any commands you wish and they will take place relative to your mounted drive.  Run the following commands to update any incomplete packages.

```
apt-get upgrade
apt-get update
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
apt-get update
apt-get upgrade
aptitude update
aptitude upgrade
```

The above commands might be a bit redundant, but it can't hurt.  Now, if you install was as botched as mine was, you'll probably run into some dependency errors while running those commands.  I had a number of packages there were not properly configured.  However, I couldn't configure them, no matter what I tried.  I solved this specific issue by deleting the temporary .deb folder which contains uninstalled packages.

```
cd /var/cache/apt/archives
sudo rm -rf *
mkdir partial
```

Then run some more upgrade / update stuff.

```
apt-get upgrade
apt-get update
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
apt-get update
apt-get upgrade
aptitude update
aptitude upgrade
```

You should no longer have an dependency errors.  This should solve most of the problems for most people.  However, if you're like me and you install was royally ****ed up, then you'll possibly need to replace a few files.  I was able to boot into Ubuntu 10.04 which was a nice feeling, but X-server was outputting a few errors.  It was spitting out some nonsense about a specific file, in my case libgdk-2.0, being too short.  I checked it out and found that it was 0 bytes.  So I copied the files from my live disk over to my hard drive and to my amazement the system booted perfectly and started xfce without fail.

I'll also note, that if you run into any errors regarding /proc/ while updating, you may need to boot into you hard drive install and run update / upgrade / dist-upgrade to fix any of those issues.  I ended up going back and forth between the live disk and my hard drive install running the same commands a million times.  Anyhow, I hope this helps someone out.  I seemed to be the only person this has happened to.

---

### Post by mörgæs on 2010-09-29
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by Stieffers on 2010-09-29
> **mörgæs said:**
> [http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

I've been through that thread but none of the suggestions are pertinent.  My hardware is supported and the machine still boots.  I'm pretty sure the only thing holding me back from fixing the botched packages is a lack of WPA protocol support through iwconfig.

---

