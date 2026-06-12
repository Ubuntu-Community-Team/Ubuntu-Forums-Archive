---
title: "upgrading and downloading on separate machines"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by rpm13 on 2008-09-09
I have an ubuntu (old dapper) on my laptop and a debian on my desktop.

I want to upgrade my laptop to hardy but I dont want it to be grinding away at the net for hours. [This Fujitsu laptop gets quite hot after about 45 minutes or so]

So is there some way to do something like

1. Ask maybe update-manager or apt-get to generate the list of debs needed for the upgrade on the laptop
2. Move that list to my desktop and download the packages there
3, Copy the packages from desktop to laptop:/var/cache/apt/archives
4. run apt-get upgrade or update-manager or some such

Any other known way of separating download from installing will also be appreciated.

Thanks!

---

### Post by Partyboi2 on 2008-09-09
Another option is to upgrade using the alternate cd. You can download it from [URL="http://releases.ubuntu.com/8.04.1/"][COLOR=Blue]here[/COLOR]
[/URL]

---

### Post by forger on 2008-09-09
> **rpm13 said:**
> 
Any other known way of separating download from installing will also be appreciated.

You could use your desktop with apt-proxy or apt-mirror
Then you could connect and configure any other computer, connect it with the desktop and pass the downloaded packages through the desktop.

[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)
[http://www.google.com/search?q=%22how%20to%22%20%22apt-proxy%22|%22apt-mirror%22](http://www.google.com/search?q=%22how%20to%22%20%22apt-proxy%22|%22apt-mirror%22)
[http://www.linux.com/feature/139213](http://www.linux.com/feature/139213)

---

### Post by rpm13 on 2008-09-09
> **forger said:**
> You could use your desktop with apt-proxy or apt-mirror
Then you could connect and configure any other computer, connect it with the desktop and pass the downloaded packages through the desktop.

[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)
[http://www.google.com/search?q=%22how%20to%22%20%22apt-proxy%22|%22apt-mirror%22](http://www.google.com/search?q=%22how%20to%22%20%22apt-proxy%22|%22apt-mirror%22)
[http://www.linux.com/feature/139213](http://www.linux.com/feature/139213)

Well... I looked these up.
-- apt-mirror mirrors the *whole set* of ubuntu/debian packages.  Thats way over the top!
-- apt-proxy evidently needs to work in 'real-time' that is to say
I will need to connect the laptop through the desktop, not to mention that the desktop will need to have two ethernet cards.

What I really need is something simpler -- like the -d option in apt-get.

---

### Post by forger on 2008-09-09
This lists the packages
```
aptitude search -F '%100p' '~U'
```
(thanks to stew @ #debian)

Example:
1) Run Ubuntu live CD, execute:
```
sudo apt-get update
```
output to a file:
```
aptitude search -F '%100p' '~U' | xargs > ~/Desktop/updatelist.txt
```

Use a USB stick (or whatever) to transfer the file updatelist.txt

2) When you transfer that file to your other computer (Desktop with Hardy) to your Desktop, we will make a directory on your desktop, where we will place all upgrades (packageupdates):
```
cd ~/Desktop
mkdir packageupdates
cd packageupdates
aptitude download `cat ~/Desktop/updatelist.txt`
```

3) Install Hardy on the laptop in the meantime.

4) When aptitude on your desktop is done downloading and your hardy on the laptop is up and running, transfer the "packageupdates" to the USB, connect it to the laptop where you have to copy the contents of "packageupdates" ```

sudo cp /media/yourusb/packageupdates/* /var/cache/apt/archives/
```
(..where you change **/media/yourusb** with the path of your usb stick or other location)

5) Update/upgrade:
```
sudo apt-get update; sudo apt-get upgrade
```

Important Note:
If you get problems because the line with the packages is too big, just make xargs parse the package names every 30-40 or so, use this command instead of the one given before:
```
aptitude search -F '%100p' '~U' | xargs -n 30 > ~/Desktop/updatelist.txt
```

---

### Post by rpm13 on 2008-09-09
Hey Thanks Forger! -- I think thats along the line I need.

Just one or two questions more before I try it.
The aptitude call generates a list even without the xargs. Why use xargs?
And whats the ~U thing?

---

### Post by forger on 2008-09-09
I edited the "how to", should be OK now.
xargs makes the a list of lines into words
> $ whatis xargs
xargs (1)            - build and execute command lines from standard input
Example:
```

echo "This
should
be
in
one
line" | xargs

```

About aptitude's search terms:
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html)
> ?upgradable	~U	 Select packages that are installed and can be upgraded. 

---

