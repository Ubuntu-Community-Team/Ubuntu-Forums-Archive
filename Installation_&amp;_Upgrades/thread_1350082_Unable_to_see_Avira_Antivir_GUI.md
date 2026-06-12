---
title: "Unable to see Avira Antivir GUI"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by ddas4 on 2009-12-08
I downloaded Avira antivir from [http://www.free-av.com/en/download/download_servers.php](http://www.free-av.com/en/download/download_servers.php) and tried installing it on Karmic with the following:
```
sudo ./install
```
It went through the installation process and i answered 'y' to everything except Dazuko ( i don't want/need on-access file scanning). Installation completed but i was not able to see any GUI. Various forums say that it should be started in the following manner:
```
sudo antivir -gui
```
 
However, with this i get a 'antivir- command not found'.
 
Some forums also state that it would ask for keyfile location, GUI installation during the installation process but i was never offered these options. Looks like it installed the command line version for me. There is a GUI folder at /usr/lib/Antivir/GUI but doesnot seem to have anything with which i can start a GUI.
 
I have spent 3-4 hours trying to figure it out on the internet ; and posting this as a last hope.
 
Please help !

---

### Post by MooPi on 2009-12-08
There is an anti-virus in the repository call "clamav". It is a solid program and easy to use through the terminal. Works fine so you don't pass along viruses to your Windows buddies. Third party AV on linux may not be the best route for a desktop. Are there man pages for Avira ?

---

### Post by ddas4 on 2009-12-09
No man pages really ; documentation is within the tar.gz file. But not of much help to get the GUI kicked.
 
I used Clamav on my Fedora installation earlier (with Clamtk GUI) but i found it extremely slow - the reason why i switched to Avira for some of my other Linux distro installations.

---

### Post by ddas4 on 2009-12-09
Ok here's the secret [http://forum.avira.com/wbb/index.php?page=Thread&threadID=101454](http://forum.avira.com/wbb/index.php?page=Thread&threadID=101454)
 
Seems the Avira folks removed the GUI v3.x onwards. Their Java based UI worked fine according to me ; but they want to cut their dependency on Java now. Until then, i guess i will go with BitDefender or ClamAV.

---

### Post by ddas4 on 2009-12-09
I went the Clamav/Clamtk way ! Seems to be running fine. But when i update, it updates the signatures & says that GUI is out of date.
 
I understand that the GUI will be updated via Synaptic but is this normal or i need to make some changes somewhere ?

---

### Post by WinExpert on 2009-12-14
i looked now for some 3 days for a way to get the GUI of Antivir working under be it Ubuntu (Karmic Koala), Fedora, or now under Mandriva.

Only after long searching does one discover that all his attempts in installing the c compiler, the GTK extensions, the dazuko package, Antivir's own applet under the contrib directory are no use.

Because Antivr removed the java gui applet because it "needed" to get away from java for some reason.

I think this is UNacceptable.

Bitdefender and even more ClamAV are NO comparison to Antivr.

Antivir is slim, small, fast, resources-saving and has got the best antivirus deifinitions among all virus killers.

I wouldn't EVER want to hog up any system with any other prodcut than Antivir. I simply refuse to "go" any "other way".

I will write a letter to Avira that they shall make a new gui for their new current versions of Avira for Linux.

What under Windoofus evryone can have a gui and not under Linux? Not a good support and ads for Linux from Avira, that's for sure.

As long as Avira doesn't have any GUI for their AV product under Linux, I simply can't install Linux on any system. I am a pro pc supporter and need EXACTLY a gui for any product. I am happy with any command shell controlled app. But a user wants a visible program with buttons and stuff.

---

### Post by mikewhatever on 2009-12-14
> **WinExpert said:**
> ...........

As long as Avira doesn't have any GUI for their AV product under Linux, I simply can't install Linux on any system. I am a pro pc supporter and need EXACTLY a gui for any product. I am happy with any command shell controlled app. But a user wants a visible program with buttons and stuff.

So you don't need the gui for yourself, but for your customers, do you? If that's the case, what does it matter if they use Clam or AVG for Linux? Last but not least, I really don't think it matters much, since most linux users probably don't run an AV anyway.

---

### Post by Soul-Sing on 2009-12-14
> **ddas4 said:**
> I downloaded Avira antivir from [http://www.free-av.com/en/download/download_servers.php](http://www.free-av.com/en/download/download_servers.php) and tried installing it on Karmic with the following:
```
sudo ./install
```
It went through the installation process and i answered 'y' to everything except Dazuko ( i don't want/need on-access file scanning). Installation completed but i was not able to see any GUI. Various forums say that it should be started in the following manner:
```
sudo antivir -gui
```
 
However, with this i get a 'antivir- command not found'.
 
Some forums also state that it would ask for keyfile location, GUI installation during the installation process but i was never offered these options. Looks like it installed the command line version for me. There is a GUI folder at /usr/lib/Antivir/GUI but doesnot seem to have anything with which i can start a GUI.
 
I have spent 3-4 hours trying to figure it out on the internet ; and posting this as a last hope.
 
Please help !

try: ```
antivir-gui
```

: [http://ubuntuforums.org/showthread.php?p=8401185#post8401185](http://ubuntuforums.org/showthread.php?p=8401185#post8401185)  #16

---

### Post by ddas4 on 2009-12-14
leoquant: i have tried antivir-gui too. The GUI is just not there during the install.

---

### Post by Soul-Sing on 2009-12-14
> **ddas4 said:**
> leoquant: i have tried antivir-gui too. The GUI is just not there during the install.

strange:
please try: ```
/etc/avguard.conf
```
edit: "# Enable and configure GUI support"
put/replace:
# Enable and configure GUI support
GuiSupport yes
GuiCAFile /usr/lib/AntiVir/gui/cert/cacert.pem
GuiCertFile /usr/lib/AntiVir/gui/cert/server.pem
GuiCertPass antivir_default

is this conf. file "available"?

---

### Post by ddas4 on 2009-12-14
The file does exist in /etc/avira/ folder. I also added the line "GuiSupport yes" to avguard.conf file - everything else that you have mentioned seemed to be in place. Then when i say "antivir-gui" -- it still says command not found.

---

### Post by WinExpert on 2009-12-14
> **ddas4 said:**
> The file does exist in /etc/avira/ folder. I also added the line "GuiSupport yes" to avguard.conf file - everything else that you have mentioned seemed to be in place. Then when i say "antivir-gui" -- it still says command not found.

Of course, just this morning, I did that too, rebooted, tried to add any AV thingy in also the UPPER start panel (oops I used i win protected word, we cannot even breathe anymore, all regulated), NADA.

... I think we can solve this. Some letters to Avira would explain to them the need of ANY Linux user of the BEST EEEEEVER AV FREEEE solution.

I use Avira now on my pc on XP and now XP64 for some SEVEN years plusminus some years. Even, when the definitions get updated over the years, this Avira finds NEW viruses in my old HUGE amount of data. I am ever more virus free. And DONT think i wouln't "really" be virus free, because never viruses get detected in time. I am TOTALLY virus free with Avira and don't plan to change my habits.

Avira is ONLY so famous and nown because it is free. This chain of cause and effect now expands to Linux.

If Avira doesn't make a new GUI version of their AV solution for Linux, they will be out of the race.:P

---

### Post by Soul-Sing on 2009-12-14
> **ddas4 said:**
> The file does exist in /etc/avira/ folder. I also added the line "GuiSupport yes" to avguard.conf file - everything else that you have mentioned seemed to be in place. Then when i say "antivir-gui" -- it still says command not found.

naah, it is all about that dazuko module....
pff: ```
sudo m-a a-i dazuko
``` etc etc...
there is a outdated thread on this forum how to deal with that dazuko module.
pff, more updated: [http://wiki.ubuntuusers.de/AntiVir](http://wiki.ubuntuusers.de/AntiVir)

it is a pain really. I would recommend: bitdefender. straightforward install.

---

### Post by WinExpert on 2009-12-14
> **ddas4 said:**
> The file does exist in /etc/avira/ folder. I also added the line "GuiSupport yes" to avguard.conf file - everything else that you have mentioned seemed to be in place. Then when i say "antivir-gui" -- it still says command not found.

... Dear DDAS, it seems you over-read a statement in THIS thread, where someone correctly (and sadly) says that Antivir sadly removed their java gui since version 3. there is sadly NO way now to get up any GUI for Avira under Linux.

But that could soon change. If they don't renew their GUI and reintegrate it, be it with the help of java or another language, they will soon fall into TOTAL OBLIVION, and I don't mean the good game, but one of those 16 evil worlds there, called "Oblivion planes".... .-))

(BTW, has anyone succesfully done it to be able to play any pc game, also a big one like Oblivion, under any Linux? I wouldn't want to give up Avira as well as many good pc games for windoofus,,,)

--> Avira makes a HUGE advertisement, REALLY few people know that by a simple cutting of permissions, one can prohibit the ads window from ever appearing again, while all updates continue normally. So most people see that ads window.

They WILL NOT EVER see it again if Avira doesn't GO THE LINUX WAY.

We dont have to go any way. We just go the Linux way. Also for me, THAT is the way to go. AWAY from CRUEL AND INJUST capitalism. Hasta la victoria siempre as commandante Che Guevara said more than once.

No, the big companies have to go OUR way OR DIE. So it is. Hehe. Avira will see for themselves.

If they don't bring up a new gui for Linux, I will change my habits concerning my software against viruses.

And when I change my way, MANY, MAAAANY others do so, too, because there is no other way to go.

Avira could make ads for even other stuff, I wouldn't care, as long as they are totally free. No one else would care about the nagging window evry 3 days or so. I cost 50 swiss franks per hour for some 12 years now, from now on, its 100 franks per hour. Shall they call me up and tell me to get rid of the stupid ads window for them. And make their pc faster and more secure.

I will try out AVG already now. How sad for Antivir. They are kinda mad removing their java support. I understand they don't want to pay license fees to java, when they are already free. But they SURELY make a LOT of dough with their ads and premium versions.

How about getting an old version to run? Not likely. Avira always updates itself to the newest program version, sadly.

ps: to the one who before told me somethin like "oh, but you have.... haven't you?": You got REALLY totally wrong prejudices against me. On top of that, you shout out you know stuff about Antivirus concerns, but in fact have got NO CLUE at ALL. It is chaps like YOU who beat me up all my life and didn't let me climb to the top, although my knowledge and know-how is far greater than most others' who are successful and earn really a LOT. I don't. Because most people who COULD be my clients are EXACTLY like YOU. Full of WRONG prejudices. I am a VICTIM of this injust society, you (SWEARWORD LEFT OUT BY ME). And YOU are the WRONGDOER here, MIND that. I DO MIND. All this just SEEMS "offtopic". Be it Avira, be it Linux-realted questions, people have got the wrong view of it all, mostly. I have the right one, it is so, now you can all come and try to bash on me, in vain! .-))

---

### Post by WinExpert on 2009-12-14
> **leoquant said:**
> naah, it is all about that dazuko module....
pff: ```
sudo m-a a-i dazuko
``` etc etc...
there is a outdated thread on this forum how to deal with that dazuko module.
pff, more updated: [http://wiki.ubuntuusers.de/AntiVir](http://wiki.ubuntuusers.de/AntiVir)

it is a pain really. I would recommend: bitdefender. straightforward install.

sudo doesn't work for me, only su root. "sudo" doesn't SEEM to "work" for me because when i type in "sudo", he asks me for a password i REALLY surely don't know. it CANNOT be the root pw I myself indicated in the install of Mandriva. But since su works, I don't even know if those two commands are the same or not, in fact, this is not the case,

then, what in heaven is " m-a " and " a-i " ?

these operands result in fails all the time.

--> EDIT: maybe I didn't yet even install dazuko, I am still somewhat unsure on linux.

I remember dazuko told me some error during avira installation.

i hope its really only the dazuko that makes the gui not work. I HOPE. I am NO linux expert (yet).

I mean, avira includes an "applet" under its CONTRIB directory. Seems contradictory to hear they "removed their gui since version 3 because of cutting their java-dependancy".

What now? Repair or fix dazuko and gui works or not?

... I looked into the link they guy right above gave: [http://www.dazuko.org/tgen.shtml#DEBIAN](http://www.dazuko.org/tgen.shtml#DEBIAN)

---< it IS a major pain in the A...  for sure. Ill post back in some days, pooo.

---

### Post by ddas4 on 2009-12-14
@WinExpert: i was the one who found from the Avira forum and posted that they want to get rid of their Java UI now
 
@leoquant: i don't have dazuko installed & enabled. So i guess, i need to wait for Avira to release their new GUI. Also, i have ClamAV installed (it's slow; needless to say). I was thinking of going with BitDefender (which is installed on one of my OpenSuse installations) but i thought since it's not a part of the standard Ubuntu repo ; i will stick with ClamAV.
 
I am marking my original question as 'solved' now.
Thanks everyone for your valuable inputs !

---

### Post by Soul-Sing on 2009-12-15
> I was thinking of going with BitDefender (which is installed on one of my OpenSuse installations) but i thought since it's not a part of the standard Ubuntu repo ; i will stick with ClamAV.

Thats a good idea, installing software from trusted ubuntu-sources. and sorry putting you on the "wrong" track with avira/antivir-gui.

---

### Post by vvuk on 2010-02-14
Sorry for writing on closed theme but I just want to inform you that AV gui is available according to this site [http://wiki.ubuntuusers.de/AntiVir](http://wiki.ubuntuusers.de/AntiVir) which is dated on 28. Januar 2010. I will check that now... I guess it's just for Server edition witch is not free

---

