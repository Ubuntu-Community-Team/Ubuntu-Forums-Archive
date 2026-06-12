---
title: "Update Manager: &quot;Failed to fetch...&quot;"
date: 2014-05-23
forum: Installation &amp; Upgrades
---

### Post by pmasson on 2014-05-23
I was prompted that updates (12.04 LTS) were available from the Updates Manager GUI. Clicking updates resulted in...

```

Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.16.1.2ubuntu7.4_amd64.deb Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/bluez_4.98-2ubuntu7.2_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/libbluetooth3_4.98-2ubuntu7.2_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre_7u55-2.4.7-1ubuntu1~0.12.04.2_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/icedtea-7-jre-jamvm_7u55-2.4.7-1ubuntu1~0.12.04.2_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre-headless_7u55-2.4.7-1ubuntu1~0.12.04.2_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.4.2-0ubuntu0.6.6_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-greeter/unity-greeter_0.2.9-0ubuntu1.3_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/bluez-alsa_4.98-2ubuntu7.2_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/bluez-cups_4.98-2ubuntu7.2_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/bluez-gstreamer_4.98-2ubuntu7.2_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_29.0+build1-0ubuntu0.12.04.2_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_29.0+build1-0ubuntu0.12.04.2_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.356ubuntu0.12.04.1_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://dl.google.com/linux/talkplugin/deb/pool/main/g/google-talkplugin/google-talkplugin_5.3.1.0-1_amd64.deb Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-locale-en_24.5.0+build1-0ubuntu0.12.04.1_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_24.5.0+build1-0ubuntu0.12.04.1_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-gnome-support_24.5.0+build1-0ubuntu0.12.04.1_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_24.5.0+build1-0ubuntu0.12.04.1_amd64.deb Unable to connect to 10.1.7.128:8080:
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-locale-en-us_24.5.0+build1-0ubuntu0.12.04.1_all.deb Unable to connect to 10.1.7.128:8080:

```

The Update Manager details stated:[INDENT]**Update Manager Details**

[I]Changes for the versions:
Installed version: 1.16.1.2ubuntu7.2
Available version: 1.16.1.2ubuntu7.4

Failed to download the list of changes. 
Please check your Internet connection.Failed to download the list of changes. 
Please check your Internet connection.[/I]
[/INDENT]

I then tried updating directly from the terminal with: ```
sudo apt-get update
```

This resulted in:

```
0% [Connecting to 10.1.7.128 (10.1.7.128)] [Connecting to 10.1.7.128 (10.1.7.128)] [Connecting to 10.1.7.128 (10.1.7.128)] [Connecting to 10.1.7.128 (10.1.7.128)] 
Err http://dl.google.com stable Release.gpg                                                                                                                                                          
  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Err http://dl.google.com stable Release.gpg                                                                                                                                                          
  Unable to connect to 10.1.7.128:8080:
Err http://security.ubuntu.com precise-security Release.gpg                                                                                                                                          
  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Err http://archive.canonical.com precise Release.gpg                                                                                                              
  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Err http://archive.canonical.com precise Release.gpg                                                                      
  Unable to connect to 10.1.7.128:8080:
Err http://ppa.launchpad.net precise Release.gpg                                  
  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Err http://us.archive.ubuntu.com precise Release.gpg                              
  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Err http://us.archive.ubuntu.com precise-updates Release.gpg
  Unable to connect to 10.1.7.128:8080:
Err http://us.archive.ubuntu.com precise-security Release.gpg
  Unable to connect to 10.1.7.128:8080:
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Unable to connect to 10.1.7.128:8080:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release.gpg  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Unable to connect to 10.1.7.128:8080:

W: Failed to fetch http://archive.canonical.com/dists/precise/Release.gpg  Unable to connect to 10.1.7.128:8080:

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg  Unable to connect to 10.1.7.128:8080:

W: Failed to fetch http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu/dists/precise/Release.gpg  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out

W: Some index files failed to download. They have been ignored, or old ones used instead.


```

I then tried to connect to another server through the settings in the Update Manager. Now when I try and update, I am warned:[INDENT][I]Update Manager Dialog Manager

Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.
Details:
bluez bluez-alsa bluez-cups bluez-gstreamer dpkg firefox firefox-locale-en flashplugin-installer gnome-settings-daemon google-talkplugin icedtea-7-jre-jamvm libbluetooth3 openjdk-7-jre openjdk-7-jre-headless thunderbird thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us unity-greeter[/I]
[/INDENT]

Not sure where to go here. My network connection is fine, and indeed when I try and connect directly to the repository through a browser, e.g. [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg), I can get there--so a network access issue does not seem to be the issue.

Any advice?
Thanks.

---

### Post by Frogs Hair on 2014-05-23
The untrusted package warning should be resolved after running the following now that you have connected to a server .```
 sudo apt-get update && sudo apt-get upgrade
```

---

### Post by pmasson on 2014-05-24
> **Frogs Hair said:**
> The untrusted package warning should be resolved after running the following now that you have connected to a server .```
 sudo apt-get update && sudo apt-get upgrade
```

Thanks F.H.,

```
ma@mymachine:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for me: 
Err http://dl.google.com stable Release.gpg                                                                                                                                                               
  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Err http://dl.google.com stable Release.gpg                                                                                                                                                               
  Unable to connect to 10.1.7.128:8080:
Err http://security.ubuntu.com precise-security Release.gpg                                                                                                       
  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Err http://archive.ubuntu.com precise Release.gpg                                                                                                                 
  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Err http://archive.ubuntu.com precise-updates Release.gpg                                                                 
  Unable to connect to 10.1.7.128:8080:
Err http://archive.ubuntu.com precise-security Release.gpg                        
  Unable to connect to 10.1.7.128:8080:
Err http://archive.canonical.com precise Release.gpg                              
  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Err http://ppa.launchpad.net precise Release.gpg                                  
  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
Err http://archive.canonical.com precise Release.gpg                              
  Unable to connect to 10.1.7.128:8080:
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Unable to connect to 10.1.7.128:8080:
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release.gpg  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Unable to connect to 10.1.7.128:8080:
W: Failed to fetch http://archive.canonical.com/dists/precise/Release.gpg  Unable to connect to 10.1.7.128:8080:
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg  Unable to connect to 10.1.7.128:8080:
W: Failed to fetch http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu/dists/precise/Release.gpg  Could not connect to 10.1.7.128:8080 (10.1.7.128), connection timed out
W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  dpkg firefox firefox-locale-en flashplugin-installer google-talkplugin icedtea-7-jre-jamvm openjdk-7-jre openjdk-7-jre-headless thunderbird thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us
13 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 118 MB of archives.
After this operation, 15.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  dpkg openjdk-7-jre icedtea-7-jre-jamvm openjdk-7-jre-headless firefox firefox-locale-en flashplugin-installer google-talkplugin thunderbird-locale-en thunderbird thunderbird-gnome-support thunderbird-globalmenu thunderbird-locale-en-us
Install these packages without verification [y/N]?
```

I guess I am wondering why these "cannot be authenticated!," I thought most are native to/supported by Ubuntu--why are these unauthenticated (maybe I don't know what that means) and should I be concerned?

Thanks

---

### Post by deadflowr on 2014-05-25
I'm wondering why all your repos are trying to connect to the same exact IP address?
All the archive.ubuntu.com lines being the same makes sense, but the google.com repo should be a completely different address.

Isn't the 10.1.7.128 a local address?
(I actually don't know, which why the question)

---

### Post by pmasson on 2014-05-26
> **deadflowr said:**
> I'm wondering why all your repos are trying to connect to the same exact IP address?
All the archive.ubuntu.com lines being the same makes sense, but the google.com repo should be a completely different address.

Isn't the 10.1.7.128 a local address?
(I actually don't know, which why the question)

Yes, according to wikipedia ([http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network))...
 [TABLE="class: wikitable"]
[TR]
[TH]RFC1918 name[/TH]
[TH]IP address range[/TH]
[TH]number of addresses[/TH]
[TH]largest [CIDR]("http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing") block (subnet mask)[/TH]
[TH]host id size[/TH]
[TH]mask bits[/TH]
[TH]*[classful]("http://en.wikipedia.org/wiki/Classful_network")* description[SUP][[Note 1]]("http://en.wikipedia.org/wiki/Private_network#cite_note-3")[/SUP][/TH]
[/TR]
[TR]
[TD]24-bit block[/TD]
[TD]10.0.0.0 - 10.255.255.255[/TD]
[TD]16,777,216[/TD]
[TD]10.0.0.0/8 (255.0.0.0)[/TD]
[TD]24 bits[/TD]
[TD]8 bits[/TD]
[TD]single [class A network]("http://en.wikipedia.org/wiki/Class_A_network")[/TD]
[/TR]
[TR]
[TD]20-bit block[/TD]
[TD]172.16.0.0 - 172.31.255.255[/TD]
[TD]1,048,576[/TD]
[TD]172.16.0.0/12 (255.240.0.0)[/TD]
[TD]20 bits[/TD]
[TD]12 bits[/TD]
[TD]16 contiguous class B networks[/TD]
[/TR]
[TR]
[TD]16-bit block[/TD]
[TD]192.168.0.0 - 192.168.255.255[/TD]
[TD]65,536[/TD]
[TD]192.168.0.0/16 (255.255.0.0)[/TD]
[TD]16 bits[/TD]
[TD]16 bits[/TD]
[TD]256 contiguous class C networks[/TD]
[/TR]
[/TABLE]
 
Looking at my Connection Information, I am 192.168.0.0 range.

I do not know why they are trying to connect through that IP either? Any ideas?

Thanks,
Patrick

---

### Post by pmasson on 2014-05-26
A bit more information...

This IP was used for a proxy server at another location. I found it referenced in
[FONT=courier new] /etc/apt/apt.conf[/FONT]

I removed that file, [FONT=courier new]apt.conf[/FONT] and also removed all the references in my browsers' preferences (Firefox and Chrome as well as Thunderbird) however when I run 
[FONT=courier new]  sudo apt-get update && sudo apt-get upgrade[/FONT]

[FONT=arial]I still see the updates trying to reference the 10.1.7... address. Where else might the proxy server be referenced, particularly were would be apt looking it up?

Thanks,
Patrick
[/FONT]

---

### Post by prmurthy on 2014-05-26
Have you confirmed that you have a working internet connection? The 10.1.x.x address range is usually a private IP address and the above suggests that your router is not connected to the Internet

---

### Post by pmasson on 2014-05-26
I've solved my issue, but as someone jumped on thi tread with another issue, I am hesitant to mark this closed/solved.

 My issue was due to environmental settings pointing to a proxy server I had to go through at another location. Apparently these were still being used by apt-get when looking for the ubuntu archive.

I first opened /etc/environment and removed the lines: 
[FONT=courier new]http_proxy="http://10.1.7.128:8080/"
https_proxy="https://10.1.7.128:8080/"[/FONT]

Then ran:
[FONT=courier new]sudo apt-get update && sudo apt-get upgrade[/FONT]

BTW, as part of my efforts I also deleted the file [FONT=courier new]/etc/apt/apt.conf[/FONT], this alone did not resolve the issue, but it might or might not be required (not sure). I just wanted to share that in case it does also need to be addressed.

---

### Post by deadflowr on 2014-05-26
> **pmasson said:**
> I've solved my issue, but as someone jumped on thi tread with another issue, I am hesitant to mark this closed/solved.


It's your thread, mark it as solved.
If someone else needs help, they can start there own thread.

Edit: I decided to move the other poster's post(s) into a new thread.
Here
[http://ubuntuforums.org/showthread.php?t=2226358](http://ubuntuforums.org/showthread.php?t=2226358)

If in the future, someone hijacks your thread, don't hesitate to report it.
Use the repost post button at the bottom left of any post, and the staff will look into it.

---

### Post by pmasson on 2014-05-27
Just an update. I just ran the Update Manager through the desktop GUI and all went as expected.

---

