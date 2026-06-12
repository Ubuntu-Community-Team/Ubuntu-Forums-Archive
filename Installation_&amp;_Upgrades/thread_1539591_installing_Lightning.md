---
title: "installing Lightning"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by accodata on 2010-07-26
Hi All

I was trying to install Lightning as an add-on with Thunderbird.

After doing some reading I was not the only one having some problems,

To Install Lightning, I needed Thunderbird 3.1, and installed on my system is 3.06.

When I did that I now get this message,

W: Failed to fetch [http://ppa.launchpad.net/eugensan/mozilla/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/eugensan/mozilla/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Can someone please help me to fix the error?

with thanks

Tracey

---

### Post by wojox on 2010-07-26
Purge Thunderbird 3.06 and install the newest one from Mozilla.

---

### Post by accodata on 2010-07-26
thank you I had thought of that... and I do that how.

I mean I know how to uninstall through the software centre, but the installation for a fresh install I am pretty thick with

:)

---

### Post by wojox on 2010-07-26
Purge Thunderbird 

Go here [Thunderbird]("http://www.mozillamessaging.com/en-US/thunderbird/") 

Download it to your Download directory.

Then open a terminal and copy and paste

```
tar xjf thunderbird-*.tar.bz2
```

Copy to your /opt directory

```
sudo cp -r thunderbird /opt
```

---

### Post by accodata on 2010-07-26
Hi

Thank you for your help

I have this message after trying to purge Thunderbird.

tracey@tracey-desktop:~$ tar xjf thunderbird-*.tar.bz2
tar: thunderbird-*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
tracey@tracey-desktop:~$ ^C
tracey@tracey-desktop:~$ 

what have I stuffed up?

with thanks

---

### Post by wojox on 2010-07-26
You need to move to what ever directory you downloaded it from

So if you downloaded to Downloads try

```
cd Downloads
```

---

### Post by uRock on 2010-07-26
Is the command for purging ```
sudo apt-get purge thunderbird
```?

---

### Post by accodata on 2010-07-26
thanks

yes it is in Downloads

tracey@tracey-desktop:~$ cd Downloads
tracey@tracey-desktop:~/Downloads$ ^C
tracey@tracey-desktop:~/Downloads$ 


thanks

---

### Post by wojox on 2010-07-26
> **uRock said:**
> Is the command for purging ```
sudo apt-get purge thunderbird
```?

Yes it is.

---

### Post by accodata on 2010-07-26
thank you for that... 

it has been purged...

Thanks for you time, I am very thick, but very thankful for your help.

---

### Post by accodata on 2010-07-26
so now do I type in terminal 
tar xjf thunderbird-*.tar.bz2
what does the * mean? I have to find it?

---

### Post by wojox on 2010-07-26
Your welcome. Did you copy it to /opt or leave it in your Download directory?

---

### Post by wojox on 2010-07-26
> **accodata said:**
> so now do I type in terminal 
tar xjf thunderbird-*.tar.bz2
what does the * mean? I have to find it?

It will unpack it and you will then have a Thunderbird folder.

---

### Post by accodata on 2010-07-26
The thunderbird file wont move to the /opt file

---

### Post by wojox on 2010-07-26
Go back into Downloads

```
cd Downloads
```

Copy it to /opt

```
sudo cp -r thunderbird /opt 
```

---

### Post by accodata on 2010-07-26
I don't know what I have done, but Thunderbird is now installed, 3.1

Thnakyou so very much

---

### Post by wojox on 2010-07-26
> **accodata said:**
> The thunderbird file wont move to the /opt file

You want to copy the whole folder.

---

### Post by accodata on 2010-07-26
nope

I didn't install it.

but i opened something in a terminal and it ran

I am so wanting to smack myself on the side of the head

---

### Post by accodata on 2010-07-26
tracey@tracey-desktop:~$ cd Downloads
tracey@tracey-desktop:~/Downloads$ sudo cp -r thunderbird /opt
[sudo] password for tracey: 
cp: cannot stat `thunderbird': No such file or directory
tracey@tracey-desktop:~/Downloads$ ^C
tracey@tracey-desktop:~/Downloads$ 


<please insert my smack in the head NOW>

---

### Post by wojox on 2010-07-26
> **accodata said:**
> nope

I didn't install it.

but i opened something in a terminal and it ran

I am so wanting to smack myself on the side of the head

Did you go to 

```
cd /opt
```

And

```
ls
```

You should see a Thunderbird folder.

---

### Post by accodata on 2010-07-26
ok, I now have the thunderbird file in  /opt

tracey@tracey-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
tracey@tracey-desktop:~$ cd Desktop
tracey@tracey-desktop:~/Desktop$ sudo cp -r thunderbird /opt
tracey@tracey-desktop:~/Desktop$ ^C
tracey@tracey-desktop:~/Desktop$

---

### Post by accodata on 2010-07-26
the terminal code stuff.

tracey@tracey-desktop:~$ cd /opt
tracey@tracey-desktop:/opt$ ls
thunderbird
tracey@tracey-desktop:/opt$

---

### Post by wojox on 2010-07-26
> **accodata said:**
> the terminal code stuff.

tracey@tracey-desktop:~$ cd /opt
tracey@tracey-desktop:/opt$ ls
thunderbird
tracey@tracey-desktop:/opt$

There it is. It's there.
 
now run ```
/opt/thunderbird/thunderbird
```

---

### Post by accodata on 2010-07-26
ok, have done that.

I can't find thunderbird, so I am thinking I have something else to do?

again thank you

---

### Post by wojox on 2010-07-26
That's weird. Try

```
cd /opt/thunderbird
```

Then 

```
thunderbird
```

---

### Post by accodata on 2010-07-26
tracey@tracey-desktop:~$ cd /opt/thunderbird
tracey@tracey-desktop:/opt/thunderbird$ thunderbird
The program 'thunderbird' is currently not installed.  You can install it by typing:
sudo apt-get install thunderbird
tracey@tracey-desktop:/opt/thunderbird$

---

### Post by Darkness Des on 2010-07-26
You have to put ./ before it, otherwise the terminal will think that it is a command and not a file. So,
```

cd /opt/thunderbird
./thunderbird

```

---

### Post by accodata on 2010-07-26
so I have to put a "." infront of where?

please

---

### Post by wojox on 2010-07-26
> **Darkness Des said:**
> You have to put ./ before it, otherwise the terminal will think that it is a command and not a file. So,
```

cd /opt/thunderbird
./thunderbird

```

Copy and paste Darkness two commands an it should work.

---

### Post by accodata on 2010-07-26
Hi

Thank you for that, when I put in those lines.

Thunderbird opens, then when I close the Terminal it closes.

---

### Post by accodata on 2010-07-26
Hi

When I do the sudo apt-get update

I get this:

tracey@tracey-desktop:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/eugensan/mozilla/ubuntu/](http://ppa.launchpad.net/eugensan/mozilla/ubuntu/) lucid/main Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
W: Failed to fetch [http://ppa.launchpad.net/eugensan/mozilla/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/eugensan/mozilla/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by wojox on 2010-07-26
Okay lets make a link for it.

Go into Main Menu

On the left click Internet

On the right click New Item

Name = Thunderbird

Command = /opt/thunderbird/thunderbird

You can also try Alt+F2

/opt/thunderbird/thunderbird

---

### Post by accodata on 2010-07-26
WOOHOO!!

Tis fixed thank you so very much.

Now I need to forget when I found the main menu thing... so I don't stuff that up to

again.

Many thanks

---

### Post by wojox on 2010-07-26
w00t w00t good job. Your Welcome. ;)

---

