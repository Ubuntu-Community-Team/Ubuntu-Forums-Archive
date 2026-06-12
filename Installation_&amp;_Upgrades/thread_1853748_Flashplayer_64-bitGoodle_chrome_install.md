---
title: "Flashplayer 64-bit/Goodle chrome install?"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by MagnetsNextToMotherboard on 2011-10-02
Hello, I'm trying to make sure I get the 64-bit version of flashplayer installed so I installed the file from their website here: labs.adobe.com/downloads/flashplayer11.html

I chose specifically under "Flash Player 11 Candidate 64-bit Installers" the, "Download plug-in for Linux 64-bit" and extracted the files to my desktop, now I have the "usr" and "libflashplayer.so" 

How do I install it to Google Chrome? I have 64-bit Google Chrome, it just doesn't have the 64-bit flash player. 

Either the terminal command or an alternative way to install it would be nice. I was going to install it from the Ubuntu Software Center, but I'm not sure if It'll be 64-bit then. Thank you.

---

### Post by dave01945 on 2011-10-02
google chrome is a .deb file so just click it and software centre will install it if you would rather install it with command line then

```
cd /path/to/googlechrome.deb
dpkg -i googlechrome.deb
```

obviously change the path to where you downloaded the .deb file and change googlechrome.deb to the name of the .deb file

and to install the flash plugin just copy the libflashplayer.so file to /opt/google/chrome

---

### Post by MagnetsNextToMotherboard on 2011-10-02
What is a .deb? I just installed it where ever it installs the default. The only thing I haven't done as default is where I extracted the flash player file I extracted it to my desktop.

---

### Post by garvinrick4 on 2011-10-02
You still have firefox installed?

---

### Post by MagnetsNextToMotherboard on 2011-10-02
Yes, I still have firefox installed. But I dislike it very mutch.

---

### Post by dave01945 on 2011-10-02
a .deb is a software install file abit like a .exe in windows if you have already installed google chrome then you just need to do the second part and move libflashplayer.so to /opt/gogle/chrome/

also how did you install google chrome

i agree with you on firefox i dislike it aswell

---

### Post by MagnetsNextToMotherboard on 2011-10-02
I installed google chrome off of the website, and chose the 64-bit version here: [http://www.google.com/chrome#eula](http://www.google.com/chrome#eula)

---

### Post by garvinrick4 on 2011-10-02
From within directory of wheren your flash is extracted run this code below or drop libflashplayer.so in /user/lib/mozilla/plugins/  (restart your browsers) Chrome will have flash along with Firefox.
Hope your removed other versions of Flash if you had installed previously.

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 
```If you have installed before and want to remove and put 64 bit rc1 just use flash aid in add-ons in firefox will remove all remnents of flash and install 64 bit if you choose it. It runs the script for you. Chrome will work also.
## If above code has you running enjoy you Ubuntu

---

### Post by MagnetsNextToMotherboard on 2011-10-02
"From within directory of wheren your flash is extracted" I don't understand this, I'm very sorry I'm new to Ubuntu.

---

### Post by garvinrick4 on 2011-10-02
If your libflashplayer.so is on your Desktop
```
cd Desktop
``````
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```

If it is in Downloads
cd Downloads
Now the code, get it where ever it is you change directorys to there (cd Desktop) or (cd Downloads) or (cd Documents)

---

### Post by MagnetsNextToMotherboard on 2011-10-02
Is there a way I can screenshot my terminal?

---

### Post by MagnetsNextToMotherboard on 2011-10-02
Is there a way to screenshot my terminal to show you guys?

---

### Post by garvinrick4 on 2011-10-02
Open firefox and go  to Tools to addons to type flash aid in search window install it as shown.
restart firefox will be a little red circle with f in the middle in upper right of firefox
screen. Click on it and choose the one of three choices to run script, the click on it and
it will do it all for you. No fuss no muss. Until you read up on what a terminal is and
how to change directorys and linux 101 things, is a pdf book in my signature that
you can read that will tell you about the file system
 Same as Windows, Linux also has a learning curve. Enjoy your Ubuntu

---

### Post by mikewhatever on 2011-10-02
> **MagnetsNextToMotherboard said:**
> "From within directory of wheren your flash is extracted" I don't understand this, I'm very sorry I'm new to Ubuntu.

Copy the libflashplayer.so file to the desktop folder, then:
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib/mozilla/plugins/
```

...when asked, enter the password and hit Enter.

---

### Post by MagnetsNextToMotherboard on 2011-10-03
I got to the step where I'm supposed to click the red circle with the f on it and I tried but it just goes blurry (The box.) and when I click it does nothing. It appears to have installed. But the box said there were updates. Is there a simple way to install it?

---

### Post by garvinrick4 on 2011-10-03
Restart firefox and then click on red circle with f in the middle and should give you 3 choices of install like rooky to advanced type selections. Select one and follow simple
instructions. If any more problems just hollar. We will get your flash installed , have you installed already once and now trying to do 64 bit?

---

### Post by Bluesan on 2011-10-03
This might be the easiest way to get 64-bit flash:

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

Edit:

It works fine with both Firefox and Chrome/Chromium.

---

### Post by F.G. on 2011-10-03
so, i use the firefox flash-aid plugin method with both my computers, they're both 64 bit machines and work with chromium. flash-aid also removes previous versions, which i think is necessary.

if you've got flash-aid installed in firefox (you can see the red circle with the 'f') you're almost done.

if you want to use screenshots it's easy, you just press the 'PRTSC' button (usually top right-ish) for the whole screen or alt+PRTSC for just a window. if you can't find or don't have that button. you can also got to: 
Applications > Accessories > Take Screenshot

---

### Post by andyvy on 2011-10-03
You can't install Chrome or Flash?

Chrome is simple, download file from [www.google.com/chrome](www.google.com/chrome) and double click on it. 32 or 64 bit doesn't matter.

Flash won't work?

Open Chrome in a new tab type:

```
chrome://flash/
```

Should see something like this;
Flash plugin	10.3 r183 /var/lib/flashplugin-installer/npwrapper.libflashplayer.so

If it says Flash Plugin - Disabled you have to install Flash.

Open Terminal;

```
sudo apt-get install flashplugin-nonfree flashplugin-installer
```

You can also delete any existing Flash installations to make sure you're doing a clean install.

```
sudo apt-get purge flash*
```

Hope that helps.

---

### Post by andyvy on 2011-10-03
Oh, also;

Maybe try Chromium [http://www.chromium.org/](http://www.chromium.org/).

In case you want to remove Chrome as well and do fresh install before Flash:

```
sudo apt-get purge google-chrome* chrome*
```

---

