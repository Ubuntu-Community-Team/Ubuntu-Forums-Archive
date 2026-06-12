---
title: "How to sneaker-net update?"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by jsandys on 2007-06-01
My in-laws Ubuntu Dapper Drake computer only has dial up access to the net.  They just did the snowbird thing and moved back from AZ.  The update manager says there is 100Meg of updates awaiting.  Can I just create a list of the packages, copy them to a thumb drive with my internet connection, then install them with dpkg?  Will bypassing the update manager this way screw things up?  Where is the list of packages that update manager will download?

The Ubuntu Hacks book describes how to set up your own repository, would it be better to create a repository with the packages I download to the thumb drive?  Has anyone written a script to automate this sneaker-net update process?  (I can't believe that I'm the only person in the world with this low bandwidth problem).  

Thanks, Jeff

---

### Post by RHTopics on 2007-06-01
Jeff,

The packages from Update Manager are stored in /var/cache/apt/archives.

Your approach of copying them to a thumb drive from your computer and then copying them to /var/cache/apt/archives on your in-law's computer will work.

Update Manager will see the packages in the archives and apply the updates without trying to download them.

I have done it when I had 2 computers using the same version of Ubuntu.

---

### Post by hartz on 2007-06-01
As RHTopics said, using dpkg is fine.

To get the list of packages, run the following "simulation upgrade" command:
```
sudo apt-get -s upgrade > /tmp/simrun
```

This will run a few seconds and generate the file /tmp/simrun.

You can display the file with the following command
```
cat /tmp/simrun
```

You can parse this file to create a concise list of packages to run with this command:
```
awk '/Inst/ {print $2}' /tmp/simrun | sort -u > /tmp/list.txt
```

This saves the listing in a file named /tmp/list.txt  - The next command can be used to view the file:
```
cat /tmp/list.txt
```

You can copy this file or email its contents to your own PC.

If the files are not already on your own computer (in the location as specified by RHTopics), then to download the packages, you can use this command (Assuming you placed the list.txt file in /tmp):
```
sudo apt-get -d install $( cat /tmp/list.txt )
```

The packages will be downloaded to /var/cache/apt

You can copy them via USB "thumb drive" to the /var/cache/apt directory on the inlaws' computer, and then let the upgrade do its magic, (it should find the already downloaded files), or you can use dpkg to install the files manually.

---

### Post by roger_wilco on 2007-07-17
You can use RASP (Rasp's A Sneakernet Proxy) to download the packages. See [http://rasp.sourceforge.net/]("http://rasp.sourceforge.net/")

It's most convenient to download the package list directly, then only use the proxy to download the packages. I recently upgraded my machine using this tool.

---

### Post by jsandys on 2007-10-23
This is what a found that works:

A) On the dial up computer:
1) Insert usb drive.
2) Dial up, Gnome PPP.
3) Start Synaptic Package Manager and select these menu items:
4) Edit / Reload Package Information
5) Edit / Mark All Upgrades
6) File / Generate Package Download Script, Name the file and select the usb drive in the Save in Folder field.

B) On the high speed internet computer:
1) Insert usb drive
2) open the terminal and enter:
3) cd /media/ <what every the usb drive name>
4) source <filename that you used above>

C) Back on the dial up computer
1) Open terminal and enter:
2) cd /var/cache/apt/archives
3) sudo cp /media/<usb drive name>/* ./
4) start Software Updates (the orange star icon)
5) click Install Updates.

Done!

If you have a windows computer for high speed internet, you can get GNU wget and make the script a batch file (.bat) by deleting the first line out of the script, and execute it with run.

---

