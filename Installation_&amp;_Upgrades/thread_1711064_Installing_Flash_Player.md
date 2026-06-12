---
title: "Installing Flash Player"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by Undermaris on 2011-03-20
[FONT=Arial][SIZE=3]Hi All, I am absolute beginner with ubuntu. I have been trying to download and install flash player with little success. I have downloaded it and according to system it is installed. However when I am on the internet and want to listen to the radio I get a message saying I need to install flash player[/SIZE][/FONT][SIZE=3]. Any help with resolving this problem would be much appreciated.

TIA Undermaris.[/SIZE]

---

### Post by mikewhatever on 2011-03-20
The recommended method to install flash player is from the software center (search for flash). Can you provide a detailed explanation of how you installed flash. It may give a clue as to why it doesn't work.

---

### Post by Undermaris on 2011-03-20
I loaded the Firefox Browser and the loaded the BBC home page. All fine so far. then when I clicked on Radio 4  then on listen live it said I needed to download flash player and went to a page on the Adobe website to allow me to download flash player. I gave me several options of which version I wanted to down load, I chose APT for Ubuntu 9.04+ . It then another downloaded it and asked if I wanted to install it I clicked on ok and it opened another window and I clicked on the install option. It seamed to be installing it ok, then said "installed" . So I assumed it was installed, but when I go back to trying to listen to the radio it says I need to install flash player in order to listen.

---

### Post by jpcode on 2011-03-20
I would use synaptic: click on System on the top left assuming you are using gnome, then Administration then Synaptic Package Manager. Search for "flash" I would use the non-free one but there are several choices and I don't know which is better. (Non-free does not mean you pay for it) click the box next to it and then select apply on the top. You should see a process for downlaoding and then applying. You will want to restart you browser and it should work.

---

### Post by mikewhatever on 2011-03-20
That installation process should have worked. Try restarting Firefox if you haven't yet.

---

### Post by grahammechanical on 2011-03-20
Here is a link from the BBC web site;

[http://iplayerhelp.external.bbc.co.uk/help/downloading/air_linux](http://iplayerhelp.external.bbc.co.uk/help/downloading/air_linux)

Note the point about need for the latest version of flash. I downloaded the latest version (64bit in my case) through the Ubuntu Software Centre. I have no problems listening to BBC radio or watching TV through BBC iplayer or ITV player. I do not use the iplayer desktop. So, I cannot comment on that.

Regards.

---

### Post by lovinglinux on 2011-03-20
Get [Flash-Aid]("http://www.webgapps.org/addons/flash-aid") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

---

### Post by Undermaris on 2011-03-21
Thanks for your reply, however I am not sure exactly how I run Flash-Aid. As I said in my original message I am a total beginner as far as Ubunto goes so need more detailed help please. I went to the Flash-Aid site as you suggesed but have no idea what options to choose or how to run them. Please can you explain once I have entered the flash aid site which option I need and how I run it. Sorry if I sound thick but like I say I loaded Ubuntu for the first time yesterday.


TIA
Undermaris

---

### Post by lovinglinux on 2011-03-21
> **Undermaris said:**
> Thanks for your reply, however I am not sure exactly how I run Flash-Aid. As I said in my original message I am a total beginner as far as Ubunto goes so need more detailed help please. I went to the Flash-Aid site as you suggesed but have no idea what options to choose or how to run them. Please can you explain once I have entered the flash aid site which option I need and how I run it. Sorry if I sound thick but like I say I loaded Ubuntu for the first time yesterday.


TIA
Undermaris


First of all, you need to install the extension. Download the latest version from the extension web site, then drag the downloaded xpi file to Firefox to install it. After installation, restart Firefox. A new icon will be added to the navigation toolbar. Click it. The extension will launch. All you need is to click the "Execute" button then. The extension will detect system version and architecture, installed flash plugins, possible tweaks and will generate a script to remove all flash plugins and install the latest beta from Adobe. It will also automatically launch the generated script in a terminal. Enter your password and it will do what it is supposed to do. You will receive a message when you can close the terminal. Restart Firefox and you will have the latest flash version.

---

### Post by Undermaris on 2011-03-21
Thank you very much for trying to help me, but I just don't understand what you are saying. You lost me right at the start of your reply when you said download the xpi file. I have no idea what that is or where to find it. Sorry to be thick but it just seems so complicated to me.
regards
undermaris

---

### Post by lovinglinux on 2011-03-21
> **Undermaris said:**
> Thank you very much for trying to help me, but I just don't understand what you are saying. You lost me right at the start of your reply when you said download the xpi file. I have no idea what that is or where to find it. Sorry to be thick but it just seems so complicated to me.
regards
undermaris

To get it, visit [http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)

A xpi file is basically a zip archive with a different file extension name. This is what Firefox recognizes as an add-on installation file. When you visit Flash-Aid page, there is a download link. The file you will get is a xpi file. After downloading it, just drag that file to a Firefox window and it will start the installation process. Is pretty straight forward. Just follow the instructions on the screen. After installing it, you will need to restart Firefox.

After restarting Firefox, the extension icon will be displayed in your Firefox toolbar. Click it. A new dialog will pop up. Click the "Execute" button in the dialog. The extension will do everything for you. You just need to enter your password when prompted by a terminal. There are instructions displayed on every step.

---

### Post by Undermaris on 2011-03-22
Thank you very much for being extremely patient with me and trying to help. I am sorry but still am not having any success.  I went to the flash-aid website via the link you gave me in your last reply. I downloaded the xpi file and installed it as you suggested. I found the new flash icon on the far righthand side of the toolbar. I clicked on that icon then on the "Execute" option as you suggested. A terminal window opened and it asked me for my supervisor password. I entered that and the script ran and terminated correctly without error. I then restarted firefox but I still get an error when I try to run flashplayer saying I have the wrong version installed, Please install correct version. So where do I go from here please??

regards
Undermaris.

---

### Post by eugid on 2011-03-22
HI, I've just had the same thing trying to listen to BBC Radio 2 today. I think you're downloading the wrong version of Ubuntu.  Go from the BBC link, and try a different version, I can't remember which one I used, I think it was the second from the bottom, and 8+  not 10+, make sure it installs not just downloads.  Good luck.

---

### Post by Undermaris on 2011-03-22
I now have it all working correctly. The one thing I had not tried since running Flash-Aid was to switch off my computer and beboot from cold. I did this and now Flashplayer is working correctly. Thanks a lot to all who tried to help me, it's very much appreciated.

Undermaris

---

### Post by lovinglinux on 2011-03-22
> **Undermaris said:**
> I now have it all working correctly. The one thing I had not tried since running Flash-Aid was to switch off my computer and beboot from cold. I did this and now Flashplayer is working correctly. Thanks a lot to all who tried to help me, it's very much appreciated.

Undermaris

You are welcome.

---

