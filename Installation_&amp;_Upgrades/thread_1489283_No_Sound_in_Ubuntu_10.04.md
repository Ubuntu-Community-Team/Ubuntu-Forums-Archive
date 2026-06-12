---
title: "No Sound in Ubuntu 10.04"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by nwu on 2010-05-20
Hey guys,

I just did a fresh install of Ubuntu 10.04 (from Windows 7), and I've noticed that I have no sound in Ubuntu--not on YouTube, not while logging in. In fact, I don't recall ever hearing any sound while running Ubuntu.

I've searched on Google for a bit, but none of the fixes online have worked for me. I've checked my sound preferences, and everything I see is maxed out.

Any ideas? Thanks.

---

### Post by atreides8081 on 2010-05-21
Try:

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```

and reboot.

(it worked for me on a sony vaio.)

---

### Post by nwu on 2010-05-22
Looks like this got me sound, BUT now my computer freezes after a certain amount of time from being booted. If I log in as quickly as possible, I have only a few seconds to do anything on the computer.

I like the sound, but not at the expense of being unable to use my computer. :/ Any way to undo this change?

---

### Post by dino99 on 2010-05-22
install paprefs and gnome-alsamixer (set your prefs)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by nwu on 2010-05-27
I had to re-install Ubuntu because of my computer freezing up.

paprefs / gnome-alsamixer didn't work for me. gnome-alsamixer didn't even show any options.

I'm currently looking through the "sound troubleshooting" link you gave me, but in the meanwhile, does anyone have any ideas?

---

### Post by fr0sty on 2010-05-27
What are you installing on? Cuz if its a HP laptop, I have had to do an audio driver update for my sound to work on an hp dv3t. heres the link to it. I wouldn't do it unless your using an hp laptop. [http://ubuntuforums.org/showthread.php?t=1159778](http://ubuntuforums.org/showthread.php?t=1159778)

---

### Post by GlennW on 2010-06-03
Hi all,

I've just lost my audio after an update. I didn't realize it at the moment since I didn't have any audio playing. (I was actually working!) However, after quickly trying to restart pulse audio (to no avail), rebooting, and the instructions in this thread, I'm still without sound. 

I installed gnome-alsamixer. When accessing it, there is nothing in the box. There's only the border that says, "Gnome-Alsamixer." When I try to access the sound card through it, it just disappears. 

System>Preferences>Sound doesn't help either. There's nothing under Hardware, nothing under Input, and Output has "Dummy Output" enabled. (I've never seen that before.) Under Applications there's Alsa plug-in (firefox-bin). 

I'm fresh out of ideas. Any one with any thoughts?

---

### Post by GlennW on 2010-06-03
Now, to make matters worse, I've lost icons off the top panel menu (which I can live with) but I've lost my internet connection. My laptop (also running 10.04 but on an upgrade not fresh install) has full connection right beside my now ailing desktop. The desktop has a USB D-Link wifi stick and has, up till now, worked flawlessly. 

Add to that the fact that I have not been able to mount my DVD, I'm pretty disillusioned with Lucid. Yes, it is quite a bit faster but these are major issues.

Any one have any thoughts?

This is just crazy. I reboot several times and now I have an internet connection again. I have sound. Now if I could just get the DVD to be recognised!

---

### Post by mkkblau on 2010-06-05
it worked without any problem. thanks

---

### Post by razvandudu on 2010-10-05
> **atreides8081 said:**
> Try:

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```and reboot.

(it worked for me on a sony vaio.)

It worked for me too, on a VIA chipset mobo (VT82xx)
Thanx :)

---

### Post by hdemarzo on 2010-12-20
This solution is not working for me.  it worked in the past but i just did a fresh reinstall , and i have no sound.  when I run this command this time i get the following

howard@howard-laptop:~$ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5
gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com
gpg: key 72B194E5: "Launchpad Ubuntu Audio Dev team PPA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
howard@howard-laptop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/universe Packages
Fetched 316B in 5s (56B/s)
Reading package lists... Done
howard@howard-laptop:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-27-generic

---

### Post by Robin Onedreax on 2010-12-31
really thnx for that last solution, it worked! i got my sound back. but thing is since i upgraded alsa from 1.0.21 to 1.0.23, the kazam screencaster is not letting me save the videos with audio... any thoughts on this one? i apreciate! :)

---

### Post by tirupati on 2011-01-31
> **atreides8081 said:**
> Try:

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```and reboot.

(it worked for me on a sony vaio.)


its worked for HP G62 also

---

### Post by arun_theeban on 2011-02-06
I was wondering why there is no sound in 10.04 on my Dell XPS 8300 and your post helped me. Thank you.

---

### Post by vkanth on 2011-02-19
> **atreides8081 said:**
> Try:

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```and reboot.

(it worked for me on a sony vaio.)

Had it not been for instructions like these, I'd been on a wild goose chase. Thanks to you I now have the sound back on, on my Sony Vaio Z690. There however seems to be a permanent problem with automatic updates where, after each update the hardware drivers are removed, i.e. I don't find any hardware listed under "Sound Preferences". :confused: 
Any ideas about what I can do about this issue?

Thanks in advance.

---

### Post by Walpy on 2011-02-28
This did the thing for me for Ubuntu 10.04 on my HP G62 laptop

```

~$ sudo aptitude update
~$ sudo aptitude install linux-backports-modules-alsa-lucid-generic

```and reboot!

(found the solution here: [http://www.uluga.ubuntuforums.org/showthread.php?t=1570060](http://www.uluga.ubuntuforums.org/showthread.php?t=1570060))

---

### Post by etiennenoel on 2011-03-01
Hi,

I have an Asus N82J and I don't have sound. I try everything recommended above and nothing work. Can someone give me clue please?
Thank you very much

Etienne

---

### Post by etiennenoel on 2011-03-01
sorry double post

---

### Post by sanket900 on 2011-05-28
@atreides8081

dude you rock..:guitar: it worked for me too, thanks \\:D/

---

### Post by tommaguzzi on 2011-08-13
> **atreides8081 said:**
> Try:

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```and reboot.

(it worked for me on a sony vaio.)

i registered on here just to post this reply
thanks for this atriedes8081 for posting this fix i've had no sound since i upgraded from 9.04. i tried all sorts and was on the verge of restarting.

i was so simple to paste your commands in the terminal one line at a time and reboot.

sound works fine now once again thanks  :D

---

### Post by arun_theeban on 2011-09-25
> **atreides8081 said:**
> Try:

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```and reboot.

(it worked for me on a sony vaio.)

This tip was a life saver! After struggling for 2 days the above solution worked me :). Thanks.

---

### Post by gaelicdarkwater on 2011-09-25
> **atreides8081 said:**
> Try:

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```and reboot.

(it worked for me on a sony vaio.)

Thanks for this.  I've been having a constant problem with losing all sound after automatic updates.  I didn't even have to repoot!  It just popped back up!  :KS

---

### Post by sarang031705 on 2011-09-27
Thank You Sooo Much atreides8081
It worked on my HP G42-372TX notebook pc
thanks...:popcorn:

---

### Post by Mike Daniels on 2011-10-01
I try the recommended above but get the message:

"E: Couldn't find package linux-alsa-driver-modules-2.6.32-34-generic"

Anyone have any ideas?

Thanks

---

### Post by cntmn8td2006 on 2011-10-01
Mike Daniels, I ran into the same problem myself. From the list, 2.6.32-34 is not on the list yet. The previous version 2.6.32-33 is included, but I don't know if that version would work. Also, I don't know when they will release a new one for your version.

---

### Post by leitz010 on 2011-10-01
I am also having the same problem on my dell mini 9.  I really don't want to upgrade to 11.04 because it is quite sluggish.

---

### Post by Maizy on 2011-10-03
Same here, i'm looking for 2.6.32-34 and it isnt there

---

### Post by rhduncan on 2011-10-05
Same here, also looking for the 2.6.32-34 version.

Does anyone know a suitable workaround?

I have been using the "sudo apt-get install linux-alsa-driver-modules-$(uname -r)" solution ever since installing 10.04, and this is the first time it has failed to work for me.

---

### Post by danellisuk on 2011-10-08
> **leitz010 said:**
> I am also having the same problem on my dell mini 9.  I really don't want to upgrade to 11.04 because it is quite sluggish.

Here's the fix / workaround for the Dell Mini 9:

[http://ubuntuforums.org/showthread.php?p=11323189#post11323189](http://ubuntuforums.org/showthread.php?p=11323189#post11323189)

---

### Post by williameboley on 2011-10-18
I have a Toshiba Satellite p105-s6024. 

I had problems with sound. No sound even on boot.

Ran all the commands in Terminal on the internet I could find. 

Scrolling through codes, comparing line by line, etc. 

Deleting, redoing, reinstalling OS. 

All to no avail.

You no what my problem was?

I updated my BIOS and BAM! Sound.

Hope this helps a Satellite user.

---

### Post by Timothy Taylor on 2011-10-21
I had posted my original problem [here]("http://ubuntuforums.org/showthread.php?t=1865143")

> **atreides8081 said:**
> Try:

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```

and reboot.

(it worked for me on a sony vaio.)

Worked for me too.
:)

---

### Post by slickwrist on 2012-05-26
> **Walpy said:**
> This did the thing for me for Ubuntu 10.04 on my HP G62 laptop

```

~$ sudo aptitude update
~$ sudo aptitude install linux-backports-modules-alsa-lucid-generic

```and reboot!

(found the solution here: [http://www.uluga.ubuntuforums.org/showthread.php?t=1570060](http://www.uluga.ubuntuforums.org/showthread.php?t=1570060))

This actually worked for me, when every other solution didn't. 

Hint to those who think upgrading will work: It doesn't.

---

### Post by carrucha on 2012-12-12
Post #2 worked for me, thanks.  Audio just disappeared out of nowhere after having a show paused for a while.  Line 3 of the instructions didn't work, had to manually type in the package.

---

### Post by pratik patodi on 2013-03-21
didn't work for me. Got an error msg: "Error reading [https://launchpad.net/api/1.0/~ubuntu-audio-dev/+archive/ppa:](https://launchpad.net/api/1.0/~ubuntu-audio-dev/+archive/ppa:) gnutls_handshake() failed: A TLS packet with unexpected length was received."

---

### Post by hmit23 on 2013-04-04
> 
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
doesn't work in my case, here the result:

> root@kimbio-laptop:~# sudo apt-get install linux-alsa-driver-modules-$(uname -r)Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-46-generic

---

