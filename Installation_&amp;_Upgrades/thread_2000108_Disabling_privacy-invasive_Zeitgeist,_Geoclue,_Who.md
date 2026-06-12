---
title: "Disabling privacy-invasive Zeitgeist, Geoclue, Whoopsie (and NTPD)"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by besouro on 2012-06-09
**Background**
Release after release, Canonical's Ubuntu is increasingly turning YOUR personal computer into a personal surveillance machine enabling ad companies, intelligence and law enforcement agencies, curious spouses and the occasional Google wifi war driver to harvest personal information on YOU. Aside from that, these processes also waste processing power, memory and internet bandwhich. A couple of weeks ago, a colleague installed Ubuntu for the first time complaining to me how slow it was running on his older computer. The reason offcourse were processes like Zeitgeist and Geoclue.
Below some guidelines on how to remove some of these programs and still maintaining some basic OS functionality.

**Commands**
The commands below remove:
_Zeitgeist_: Zeitgeist is a service which logs the user's activities and events (files opened, websites visited, conversations hold with other people, etc.) and makes the information available to other applications.
_Geoclue_: GeoClue is a software framework that enables geospatial awareness in applications. In human language: physical location tracking software.
_Whoopsie-daisy_: Daemon that submits (sensitive?) crash data to the Ubuntu server.

```
sudo apt-get remove zeitgeist zeitgeist-core zeitgeist-datahub python-zeitgeist rhythmbox-plugin-zeitgeist geoclue geoclue-ubuntu-geoip geoip-database whoopsie
```

**GeoClue**
Because geoclue has been intertwined with indicator-datetime, you won't be able to see the time in Ubuntu anymore. To overcome this, you can download the original sources ([https://launchpad.net/indicator-datetime/0.4/0.3.94/+download/indicator-datetime-0.3.94.tar.gz](https://launchpad.net/indicator-datetime/0.4/0.3.94/+download/indicator-datetime-0.3.94.tar.gz)) of indicator-datetime, replace "src/datetime-service.c", "configure.ac" and "configure.ac" by the ones located in the archive here: [http://www13.zippyshare.com/v/18551510/file.html](http://www13.zippyshare.com/v/18551510/file.html). Then offcourse, recompile it and install it. All references to GeoClue have been removed. For the lazy people, a deb "executable" is also included. Installing deb files downloaded from the internet is a very bad practice as they can contain rootkits!

The SHA1 checksum of indicator-datetime_0.3.94.0.1.zip is "42962afcfd56ec8277ae007c90f740f6b99388c0"
To compare the checksum:
```
sha1sum indicator-datetime_0.3.94.0.1.zip
```

**Zeitgeist**
Removing Zeitgeist will cause Unity to malfunction. As I've never been a fan of Unity I didn't care. Installing Gnome3 goes as follows:
```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell gnome-tweak-tool
sudo reboot
```

**NTPD**
To disable NTP call home requests on every Ubuntu boot, the following can be performed
```
sudo gedit /etc/default/ntpdate
```
On the first line, insert a new line containing:
```
exit 0
```

Note that your system time won't be updated automatically anymore from now on so you'll have to do this manually.

**Result**
After all the above has been performed, only the occasional connection to the following server domains will occur, mainly for keeping your Ubuntu version secure and up to date:
[LIST]
[*]extras.ubuntu.com
[*]ppa.launchpad.net
[*]changelog.ubuntu.com
[*]security.ubuntu.com
[*]ubuntu.mirrors server
[*]archive.ubuntu.com
[/LIST]

The following domains won't be contacted anymore
[LIST]
[*]ntp.ubuntu.com	(only once at boot time)
[*]daisy.ubuntu.com (sporadically called during user session)
[*]geoip.ubuntu.com (sporadically called during user session)
[*]videasearch.ubuntu.com (Sporadically called during user session, don't know why it's even used let alone by which process. If someone can enlighten me, I'd be happy to learn.)
[/LIST]

---

### Post by atenz on 2012-07-03
That was really Helpful , thanks for In-depth Info on disabling them.:KS

---

### Post by dino99 on 2012-07-03
no needs to fail into paranoia, removing zeitzeist is enough, and whoopsie is really for the best

---

### Post by rbo83 on 2012-08-20
For Whoopsie, you can set the /etc/default/whoopsie configuration file to 'false'

---

### Post by MttJocy on 2012-08-26
On the subject of ntp here for those who are truly concerned about this but would still like to actually have their time updated there are plenty of public NTP servers around you could install the NTP package and use those, or there is always the ntp pool if you don't feel like selecting servers independently yourself [http://www.pool.ntp.org/](http://www.pool.ntp.org/)

The latter are all volunteer servers which donate their services to the pool which has some several million users, I actually run two pool servers myself and it is not unusual to see 100,000 active clients on each of those on their own.

Here is a basic NTP config file which will suffice for using the pool those you might want to change the addresses to your local country zone, there is more information on the pool website

```

# --- GENERAL CONFIGURATION ---
server pool.ntp.org
server 1.pool.ntp.org
server 2.pool.ntp.org
server 3.pool.ntp.org

# Drift file.

driftfile /etc/ntp/drift

```

If you want to restrict access to your NTP server then you will want to add some restrict statements, I'll include a few examples but you should change the addresses to match your own setup.  Note: If you are behind NAT then this is not necessary unless you are running on a machine configured as DMZ or with port 123 UDP forwarded to it.

```

# If you only have the one computer and NTP is running on the same machine then you can just have a default ignore statement.

restrict default igonre

```

```

# If you have several machines on a LAN then I'd suggest the following:

restrict default ignore

# Permit hosts on network 192.168.0.0 with netmask 255.255.255.0 change these if your network is different.
restrict 192.168.0.0 mask 255.255.255.0 nomodify

```

Then just change the pool server addresses in the configuration files of your other machines to server <your main server ip>

IPv6 address ranges can be permitted the same way, if anyone has any issues I am on the pool mailing list as are a bunch of other helpful people.

Hope that helps.

---

### Post by Ubunterrific on 2012-10-12
Yes, a little on the paranoid side, OP, but i really appreciate the post because i was getting sick of geoclue-ubuntu-geoip showing up and pinging out all the time, when i've always set the time settings to manual. 

As far as i'm concerned, trimming the excess is a good thing towards efficiency.

I was just perusing the code on launchpad for mentionings of 'geo' in indicator-datetime (geoclue seriously needs to stop being a dependency already - i did read somewhere that it was going to be dropped for quantal?) So your files are a big time saver :)

As far as privacy goes - zeitgeist isn't evil. Have a quick look at the omgubuntu article for some good points: [http://www.omgubuntu.co.uk/2012/08/is-zeitgeist-spying-on-you](http://www.omgubuntu.co.uk/2012/08/is-zeitgeist-spying-on-you)

Nothing wrong with your suggestions at all, OP, i hope these tweaks do eventually become simply checkboxes or something, so the user has full say in what is going on behind the scenes - it's a vital part of the linux ethos to have the OS exactly as you want it. 

Thanks :popcorn:

---

### Post by cybrsaylr on 2012-10-12
Interesting thread, I was also interested in disabling some things after noting in 12.04 how easy it is for all your recent activities to be seen!
 All recent activity is easily seen by default, merely by clicking on Dash Home on top left launchpad! 

However by going into 'privacy' you are taken to 'Zeitgeist Activity Log Manager' which gives you the option to delete all sorts of recent things, files, apps, history and even allows you shut off recording all log activity.
[IMG]http://s13.postimage.org/ot65t2btx/image.png[/IMG]

The question in does disabling and turning off the 'Record Activity' really do this, or is it still being secretly logged somewhere else hidden deeper inside Ubuntu?

---

### Post by twogeo on 2012-10-21
Thanks to the OP for the time indicator deb.
Works fine in Unity 2D, ftr.
And Unity 2D works well enough without Zeitgeist.    Gnome-do does plenty good enough indexing of a plain desktop workflow, and it runs fine under Unity 2D.

For those who infer paranoia from the desire to keep services pared down - - it's not paranoia for me, but a fear of having to battle my way through a list of opaque processes when I may have no choice but to understand them - when for example troubleshooting something misbehaving..... memories of grinding through the set of default services running in Win machines are still not remote enough!

---

### Post by greatsirkain on 2012-11-25
good stuff, I'd already got rid of geo and zeit but it's nice to have confirmation,  think I'm going to leave whoopsie for now, can't be a bad thing to report programs and devices that are sucky. Not bothered about unity either, it's too laggy.  ):P

---

### Post by RH9R on 2012-12-07
Besouro, Thank You so much for posting. 
 
Without some post on security implications of latest codesets, only the techie gets to have any clue about the subject. As one of the 'lazy', I'm nervous about disabling a window mgr w/out more study. If you run across more on the topic(s), I hope you will continue to post.

---

### Post by RH9R on 2012-12-13
On learning to set date/time w/out npt, I stumbled into the issue of ssl certs. Technically astute can smile.
So in advanced tabs of firefox, I find a long list of certs from banks w/ verbage that seems like it was part of the orig. install. WhyTF would these be there? Are they part of orig. install? Why? Paid inclusions?

---

### Post by jerremy-tamlin on 2013-01-05
Thanks heaps for the fantastic post.

My position on the paranoid<->convenience scale is that I'm quite happy for 'MY' computer to log things, such as conversations, files opened, etc. It's my computer after all and no one uses it but me. However, because it's completely opaque when, how and by what process this data is being used I start to get fearful.

I certainly DO NOT want this private identifiable info being transmitted over a network!

What I'd really like is for developers to implement some low down privacy framework similar to android's "This application wants to access..." but better, in that it should allow fine grained selection: "Yes Google Search, I don't mind you knowing which state I'm located in but No you can't have access to my recent files list."

The other day I was at the fruit and veg shop and I wanted to scan a 'QR' code. However, the first 5 apps I went to download on my android all wanted full access my contacts! "What! Why?" I thought "I just want to know what this code on this tomato means not send that info to all my friends!"
Finally I found one that didn't need to access my contacts and used that. Of course I later discovered that what the first 5 apps were probably wanting was the ability to 'let me' send QR business cards. So nothing sinister really but because no REASONS were given I had to either COMPLETELY trust the makers of the app or NOT AT ALL.
I'd be really happy if I could install a program on ubuntu and disable it's access to a bunch of things that I don't understand why it needs and when I discovered what parts of it don't work because it doesn't have the information it needs, THEN and ONLY THEN grant it access.
I'm sure this is possible, it's what modular programming is for right?

The Linux filesystem standard has done this sort of thing wonderfully for years. Think about it, what can you do with a file? You can READ it, you can EXECUTE/RUN it, and you can WRITE/ERASE it. The filesystem give us these permission options separately for the OWNER of the file, the Super Owner/administrator/ROOT, and for OTHERS, everybody else.

Since a program runs with the same permissions as whoever ran it that means that when you run a program that program is allowed to access any of the files you are! It's like giving a robot the keys to your office, home, car and safe. Do you fully trust who built the robot?

The good news is that with open source software ANYONE can look at how the robot is built and what it's programmed to do, so if it's an *Evil Robot* hopefully someone will notice. :D

But I'd still feel better if I could choose WHICH rooms I let the robot into.
---
It's all about NOT assuming we know what other want.

---

### Post by bloodymind on 2013-01-12
Other than NTPD is any of the other softwares necessary for an ubuntu server ?

---

### Post by M8R3eob3b on 2013-03-17
Thank you very much for your post!   

> **besouro said:**
>  The SHA1 checksum of indicator-datetime_0.3.94.0.1.zip is "42962afcfd56ec8277ae007c90f740f6b99388c0"  
  I downloaded the File "indicator-datetime_0.3.94.0.1.zip" and it has a different checksum (sha1sum: da39a3ee5e6b4b0d3255bfef95601890afd80709). That is why i did not complete the last steps. I am very new to Ubuntu and Terminal and i am no native english speaker. Maybe you can upload the original File for me and others in a post?  


Btw, i am trying out Linux because i care about privacy and read Linux would be the most privacy friendly system. It is sad that Ubuntu is also establishing connections in the background without asking. At least they could give you a choice. I do not think the most people do not care. I think the most people accept it because they do not know about the dimensions of data different companies are collecting or about the possible abuses coming with it. Maybe they simply think there was no other way or they just do not care. If Ubuntu was asking me if it could connect to this or that server for this and that reason i probably would allow it. But it seems to become as a matter of course to collect data of us and our behavior without any transparency or moderation, just with a hidden link to some instructable privacy policy.

If software is sending data off a computer or a device it should ask the owner before. The question is not if the data is useful or not, the question is why should i trust in a system, which is using my line without asking me? Without letting me know even? 
(i.e. Maybe i feel secure by surfing the web via VPN in a open W-Lan Hotspot with many other strangers and than Linux is connecting to its servers, letting possible cracker know which system and what software i am using, maybe other information's i do not even know about.)   

Under OS X the snake oil "little snitch" gave me at least the feeling i had the control over outgoing connections. I never caught the system or any software connecting to the internet without "litte snitch" were asking my before if i want to allow it or not. And nearly every software is using the internet without asking. Is there a tool like that for Linux? I know it will not help against real spyware or hackers but it was helping me by controlling outgoing connections.

---

### Post by chrisinpants on 2013-03-26
It seems that removing Geoclue will break google chrome (on Arch), here:

[COLOR=#333333][FONT=sans-serif]'I have geoclue required by libwebkit, so if it's not directly from chrome, you won't be able to use chrome without it (but AUR might have a patched version)'
[/FONT][/COLOR]
from:
[URL="http://bbs.archbang.org/viewtopic.php?id=3455"]
http://bbs.archbang.org/viewtopic.php?id=3455[/URL]

---

### Post by lspells on 2013-04-16
Okay, so I didn't go quite this far, but after a lot of reading, I did write a little script to get rid of zeitgeist and whoopsie, harden the OS against external attack, make sure we aren't allowed to do IP forwarding and restrict access to the geo-ip servers that sit behind geoip.ubuntu.com (mulberry.canonical.com and mistletoe.canonical.com).  You can see what I did here and why:  [FONT=Calibri][http://foxtrot7security.blogspot.com/2013/04/ubuntu-linux-improving-privacy-and.html](http://foxtrot7security.blogspot.com/2013/04/ubuntu-linux-improving-privacy-and.html)[/FONT]

And you can pickup the script at:     
[http://code.google.com/p/pangolin-lockdown-utility/](http://code.google.com/p/pangolin-lockdown-utility/)

---

### Post by F27 on 2013-05-12
Here's the obscure automatic connections guide i made (because it's so big, i thought it would be better to start a new thread):
[http://ubuntuforums.org/showthread.php?t=2144464](http://ubuntuforums.org/showthread.php?t=2144464)

---

### Post by Ann_Onymous on 2013-08-22
While I don't subscribe to the OP's assumption that Ubuntu phoning home automatically equals a concerted effort to track our computer use...  I am very concerned about how Ubuntu 12.04 works, to the point of having to not use it.

I've run through pretty much all the possible means of removing/disabling things like ntpdate, zeitgeist, whoopsie, apport, ubuntuone and geoclue (the method on this post doesn't keep the clock now but can still remove execute permissions).

However, even after disabling auto-update, on every boot it keeps trying to connect to the repositories.  Maybe the traffic is harmless, I'm not experienced in things like reading through packets to check, perhaps it's encrypted/encoded anyway but that's not the point.

Whatever your angle or approach to security, performance and privacy, the common assumption seems to be that Linux is secure and configurable, you can throw out what you don't need and it's untainted by talk of PRISM tracking built into the (mainly) US supplied commercial operating systems.  Yet I can't seem to prove this with Ubuntu (or Mint which is worse, loading a google page every 15 mins even after telling it to "ping" elsewhere); I can install Debian an watch it sit there like it should, not trying to phone home but my compromise is Flash video on websites and Debian doesn't seem to do that so well :(
[I]
Anyway[/I], I'm not going to steam in accusing Canonical of a conspiracy theory but I what I would ask is that controls are provided for what security minded folk would see as an attack vector, what performance freaks call crap and what paranoid folk see as tracking:


[LIST]
[*]Not including Geoclue in Privacy settings could be seen as more than an oversight, as could be making it a dependency for indicator-datetime. 
[/LIST]
 

[LIST]
[*]Having dash connect to the internet for various things should be easily configurable, rather than heavy reading for new users.  It should definitely not require you to grab packages to resolve it (and therefore go online before you can disable it). 
[/LIST]
 

[LIST]
[*]Removing UbuntuOne should mean removing UbuntuOne, removing it in software centre doesn't do it, even after cleaning up the remainder in synaptic leaves the dependency tied oneconf-service which eats 30MB of RAM. 
[/LIST]
 

[LIST]
[*]Disabling automatic updates should mean not connecting to the repos on boot with no intervention, WTF! 
[/LIST]
 

[LIST]
[*]From a more personal point of view I'd do something about Rhythmbox connecting to it's various enabled plugins before you can disable them, although you can at least disconnect beforehand (although I doubt most even realise it makes these unnecessary connections).  I have similar feelings about Firefox's default config, setting a permanent cookie with Google and sending them your browser fingerprint when loading the default home page as one of many possible examples. 
[/LIST]
 
I really want to use Ubuntu but I can't use something I don't trust.  Maybe if I were more technical and a masochist I could read through all the source code and be sure but I've already spent far too much time watching traffic out of so many OS's and applications.  In an ideal world there'd be sensible defaults or prompts before being potentially compromised, I suppose a few easily discoverable settings would suffice and even at a stretch with no other option I butcher the install to meet my ends but even that isn't available.

Anyway, despite the negative nature of this message, I really like how much works out of the box in Ubuntu, things like the top of windows integrating into the UI is great even if I’m not keen on the vertical launcher, I was willing to use Unity over Gnome even with the differing preference but sadly this all becomes irrelevant for someone who wants control over their computer. I sincerely hope you make it possible to market yourselves to the general public as a genuine alternative to the OS's with hidden tracking built in; I think an educated public would want that if they knew what they're exposing themselves to but with a tired heart and mind I give up for now and look elsewhere.

---

### Post by echo6-uk on 2013-09-01
What happened to the Privacy settings that were existent on 12.04 under System Settings but are no longer available in 13.10?

---

### Post by tneiva on 2013-10-23
> **echo6-uk said:**
> What happened to the Privacy settings that were existent on 12.04 under System Settings but are no longer available in 13.10?

I have a clean install of Saucy, and all the settings for privacy are there:
-Turn on/off file and application usage
-clear usage data...
-turn off web search
-turn off error reporting

---

### Post by jrkhnt on 2013-12-06
I have just done a clean install of 13.10 on the 6th November and there are no privacy settings available. Is this just a bug or have they been removed?

---

### Post by deadflowr on 2013-12-06
> **jrkhnt said:**
> I have just done a clean install of 13.10 on the 6th November and there are no privacy settings available. Is this just a bug or have they been removed?

Where are you looking?
The settings are in system settings > privacy(or security and privacy)
The privacy settings are only in Unity.

---

### Post by vw16v on 2014-04-21
Hi, I've been happily running Ubuntu 12.04 LTS with Windows 8.1 Dual boot for about 5 months now. I just started to notice this Zeitgeist logging software recently on my 12.04 load. I recall seeing this on another distro before and thought the name seemed strange. Anyway, I haven't followed this guide to try and strip it out yet because it sounds like somewhat of a pain. 

I went into Software Center and click uninstall but it's still running>
```
bond@asus:/var/log$ ps aux|grep zeit
bond     2239  0.0  0.1 417768  5968 ?        Sl   Apr20   0:00 zeitgeist-datahub
bond     2247  0.0  0.1 348376  4960 ?        Sl   Apr20   0:00 /usr/bin/zeitgeist-daemon
bond     2254  0.0  0.2 245728  9184 ?        Sl   Apr20   0:00 /usr/lib/zeitgeist/zeitgeist-fts
bond     4366  0.0  0.0  13596   940 pts/1    S+   21:28   0:00 grep --color=auto zeit


```

It's disconcerting to see these processes still running after uninstalling it. Doing a quick locate zeitgeist in terminal also shows active .db logging files. I was going to try to install sqlite to view the .db files it's logging in this folder>

~/.local/share/zeitgeist/fts.index


I suppose I could reinstall it and install the Activities and Privacy Manager Tool to see what events it's logging and try and disable them like that. Seems a little nefarious if you ask me. My SUSE load isn't running any Zeitgeist logging. 

Thanks for any other input on a clean removal that might allow Unity to still function.

---

### Post by grumblebum2 on 2014-04-22
Nothing nefarious about zeitgeist.
It's just a data logger to enhance the unity experience.
Doesn't phone home.
Use the privacy manger to limit what it logs.

If you want to remove go back to the first post in this thread for the command to remove zeitgeist components.
> **besouro said:**
> Removing Zeitgeist will cause Unity to malfunction. As I've **never been a fan of Unity I didn't care**

Have a read...
[**_[COLOR="#B22222"]is-zeitgeist-spying-on-you[/COLOR]_**]("http://www.omgubuntu.co.uk/2012/08/is-zeitgeist-spying-on-you")

---

### Post by vw16v on 2014-04-22
> **grumblebum2 said:**
> Nothing nefarious about zeitgeist.
It's just a data logger to enhance the unity experience.
Doesn't phone home.
Use the privacy manger to limit what it logs.

If you want to remove go back to the first post in this thread for the command to remove zeitgeist components.


Have a read...
[**_[COLOR=#B22222]is-zeitgeist-spying-on-you[/COLOR]_**]("http://www.omgubuntu.co.uk/2012/08/is-zeitgeist-spying-on-you")

Thanks for this info. I'll review this website. I find it kind of ummm, funny, that they name this program after a conspiracy based documentary they have on the internet and expect you to trust it. 

I'll go ahead and reinstall it and then install the Activities and Privacy Manager Tool to see if I can get a better understanding of what it's doing. After that I'll attempt to remove this from my system. If it hoses up Unity I'll probably just remove Ubuntu and go to another load that doesn't have this crap. 

I also find it kind of funny that I removed it yet the daemon remained on my system actively logging information.

---

### Post by QIII on 2014-04-22
I suspect Zeitgeist is named from the same German word as the movie, not the movie itself.

Zeitgeist is the popular cultural spirit of the time, so it's not such a bad name for something that helps you keep track of what you've been doing.  Notice I say "you".  It doesn't phone home and gossip to everyone about what you have been doing.

"Zeitgeist" implies nothing necessarily evil to those of us who speak German.

---

### Post by grumblebum2 on 2014-04-22
> **vw16v said:**
> Thanks for this info. I'll review this website. I find it kind of ummm, funny, that they name this program after a conspiracy based documentary they have on the internet and expect you to trust it. 

I'll go ahead and reinstall it and then install the Activities and Privacy Manager Tool to see if I can get a better understanding of what it's doing. After that I'll attempt to remove this from my system. If it hoses up Unity I'll probably just remove Ubuntu and go to another load that doesn't have this crap. 

I also find it kind of funny that I removed it yet the daemon remained on my system actively logging information.
The word [**_[COLOR="#B22222"]Zeitgeist[/COLOR]_**]("http://en.wikipedia.org/wiki/Zeitgeist") was around long before some obscure film 
used it as the title.
Yeah I'm thinking of going to another distro too where there isn't so much paranoia and misinformed crap. 8-[

---

### Post by vw16v on 2014-04-23
Thanks for the replies on the term Zeitgeist. I was pretty sure it had somethign to do with a cultural movement or something else aside from the conspiracy films on the net. Either way, it's a strange name for a logging process and the name is suspect in itself if you ask me. 

I'm sticking with my original assumption that this software is undesireable and nefarious. 

Does anyone know of any linux software that shows network connections to applications and prompts you when they are attempting to be made? My windows AV always prompts me whenver applications attempt to make connections so I can determine if I'll allow the connection or not?

I've always trusted Linux freeware for some strange reason thinking that malware /rootkits,etc and not very prevelant in Linux but I'm somewhat doubtful it's as secure as everyone thinks.

However, when you get something for free you have to ask youself... Is this really free?

Which leads me to this blogpost>
**[When something online is free, you&#8217;re not the customer, you&#8217;re the product.]("http://blogs.law.harvard.edu/futureoftheinternet/2012/03/21/meme-patrol-when-something-online-is-free-youre-not-the-customer-youre-the-product/")**

All your ONES AND ZEROS BELONG TO US. LOL :twisted:

---

### Post by sam_baker2 on 2014-04-23
here are some links:

[http://linuxaria.com/howto/how-to-remove-zeitgeist-in-ubuntu-and-why?lang=en](http://linuxaria.com/howto/how-to-remove-zeitgeist-in-ubuntu-and-why?lang=en)
[http://ubuntuforums.org/showthread.php?t=2062843](http://ubuntuforums.org/showthread.php?t=2062843)
[http://www.insanitybit.com/2012/07/17/removing-zeitgeist-sped-up-unity-2/](http://www.insanitybit.com/2012/07/17/removing-zeitgeist-sped-up-unity-2/)
[http://catlingmindswipe.blogspot.com/2012/05/how-to-enhance-privacy-with-zeitgeist.html](http://catlingmindswipe.blogspot.com/2012/05/how-to-enhance-privacy-with-zeitgeist.html)
[http://iloveubuntu.net/activity-log-manager-08-handy-gui-blacklisting-zeitgeists-activity-released-ppa](http://iloveubuntu.net/activity-log-manager-08-handy-gui-blacklisting-zeitgeists-activity-released-ppa)

I use xubuntu & I took it out, but I had to leave a library in to allow gedit to work.
I have heard that in unity on 12.04 that if you took it out, things like the clock app would not work.

---

### Post by grumblebum2 on 2014-04-23
> **vw16v said:**
> Thanks for the replies on the term Zeitgeist. I was pretty sure it had somethign to do with a cultural movement or something else aside from the conspiracy films on the net. Either way, it's a strange name for a logging process and the name is suspect in itself if you ask me. 

I'm sticking with my original assumption that this software is undesireable and nefarious. 

Does anyone know of any linux software that shows network connections to applications and prompts you when they are attempting to be made? My windows AV always prompts me whenver applications attempt to make connections so I can determine if I'll allow the connection or not?

I've always trusted Linux **freeware** for some strange reason thinking that malware /rootkits,etc and not very prevelant in Linux but I'm somewhat doubtful it's as secure as everyone thinks.

However, when you get something for free you have to ask youself... Is this really free?

Which leads me to this blogpost>
**[When something online is free, you&#8217;re not the customer, you&#8217;re the product.]("http://blogs.law.harvard.edu/futureoftheinternet/2012/03/21/meme-patrol-when-something-online-is-free-youre-not-the-customer-youre-the-product/")**

All your ONES AND ZEROS BELONG TO US. LOL :twisted:
 freeware is a term usually used to describe closed-source applications.
You should really acquire the skills and knowledge to write about such matters or leave it to those that do.
Just a bundle of irrelevant disconnected tripe.

I'm sticking with my original assumption that you're undesireable and nefarious.

---

### Post by weaseldb83 on 2014-04-23
Thanks. I tried this for KDE Mint 16, thankfully none were installed.

Either way I'm thankfull you posted this as my server edition had them.

---

### Post by TOP_POT on 2015-02-23
"[COLOR=#000000]Aside from that, these processes also waste processing power, memory and internet bandwhich. "
This is the only reason I need to disable zeitgeist. So in /etc/xdg/autostart is found the file: [/COLOR]  zeitgeist-datahub.desktop
Issuing the following command will disable zeitgeist which is the purpose of this post:

sudo mv  zeitgeist-datahub.desktop zeitgeist-datahub.desktop.bak

Since there is no program called zeitgeist-datahub.desktop.bak the autostart script will happily bypass this step and it can easily be undone if desired. This approach avoids the collateral problems using apt-get remove causes with dependencies. 

I don't find geoclue on this install. 

For me using whoopsie helps provide better updates. I believe the information being shared can be selected by the user. 

Using Lubuntu 14.04

---

