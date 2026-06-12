---
title: "ie4linux will not install on lucid"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by nexx on 2010-05-01
Every times I try to execute ies4linux there is a segmentation fault. If I try to execute install.sh the console briefly appears and then shut down.
Running install.sh was the recomended installation and worked before.

---

### Post by barretr on 2010-05-02
Same result here, nexx. Fortunately there's [winetricks]("http://wiki.winehq.org/winetricks").

---

### Post by Stoneface on 2010-05-10
I have installed IEs4Linux successfully. It was a bit tricky as I had to use a different installation option, but I got it to install. I think it was using: ```
./ies4linux &#8211;no-gui.
``` that did the trick. Maybe [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux) can help you guys too if that does not work.  My currently installed IEs4Linux | Internet Explorer 6 does sometimes run and sometimes not. Restarting Ubuntu Lucid Lynx (10.0.4) helps. I do not see any errors in dmesg when it does not start. And it often does not restart properly during the same Gnome session after closing IE6 and trying to restart it. It sometimes crashed too consuming all memory until Ubuntu takes care of the issue with a ```
$ dmesg | grep -i iexplore.exe
[ 8176.861869] Killed process 2985 (IEXPLORE.EXE)
``` I wonder where the errors are stored when IEs4Linux does not start properly. Another annoying thing is that the mouse pointer often disappears hovering over the page.

---

### Post by nexx on 2010-05-15
sylvain@sylvain-laptop:~/programmes/ie4linux$ '/home/sylvain/programmes/ie4linux/ies4linux-2.99.0.1/ies4linux' --no-gui

Just use: ./ies4linux --no-gui instead of: ./ies4linux -no-gui

Had to restart the installation many times because of corrupted data form microsoft.
I also have the same mouse problem: the pointer often disappears when hovering over the page.

---

### Post by BryanFRitt on 2010-05-28
Still no luck on installation (for me at least)...

[FONT="Courier New"]./ies4linux[/FONT]

"[COLOR="Red"]IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).[/COLOR]"

"The program 'ies4linux-gtk.py' received an X Window System error.               
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 4392 error_code 9 request_code 65 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)"

[FONT="Courier New"]./ies4linux --no-gui[/FONT]
...
"[COLOR="Red"]Your wine does not have wineprefixcreate installed. Maybe you are running an old Wine version. Try to update it to the latest version.[/COLOR]"

[FONT="Courier New"]wineprefixcreate[/FONT]
   
The program 'wineprefixcreate' is currently not installed.  You can install it by typing:                                                                       
sudo apt-get install wine1.2 

[FONT="Courier New"]sudo apt-get install wine1.2[/FONT]

Reading package lists... Done
Building dependency tree 
Reading state information... Done
wine1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

p.s. it's ie**s**4linux, not ie4linux

---

### Post by valbaca on 2010-06-04
> **BryanFRitt said:**
> 
"[COLOR="Red"]Your wine does not have wineprefixcreate installed. Maybe you are running an old Wine version. Try to update it to the latest version.[/COLOR]"

[FONT="Courier New"]wineprefixcreate[/FONT]
   
The program 'wineprefixcreate' is currently not installed.  You can install it by typing:                                                                       
sudo apt-get install wine1.2 

[FONT="Courier New"]sudo apt-get install wine1.2[/FONT]

Reading package lists... Done
Building dependency tree 
Reading state information... Done
wine1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

p.s. it's ie**s**4linux, not ie4linux

I got to the same error and then tried winetricks. It works perfectly.

---

### Post by fullofbeans on 2010-06-09
> **nexx said:**
> Every times I try to execute ies4linux there is a segmentation fault. If I try to execute install.sh the console briefly appears and then shut down.
Running install.sh was the recomended installation and worked before.

I have the same problem can anyone help):P

---

### Post by decoherence on 2010-06-13
> **fullofbeans said:**
> I have the same problem can anyone help):P

don't use ies4linux anymore. get winetricks from the repository if you don't already have it. run 'winetricks' at the command line and eventually you'll get a wine window where you can install ie6 and 7 at least.

---

### Post by nexx on 2010-06-15
Tried winetricks, but it is worse than ie4linux, winetricks internet explorer 6 and 7 (yes I have time to waste) both are worse than when I use ie4linux. 

I want this for testing my search-engine: [www.artimap.com](www.artimap.com)

But now I am so pissed off by internet explorer 6 that I am beginning to think that if some peoples are using that crap to access my website they just can go to H..L :guitar:
Anyway ie6 will be dead soon !!! YOUPPI
Since I am develloping that search-engine alone I do not have time and patience for figuring those microsoft crappy problems.

---

### Post by rtimai on 2010-08-22
Just wanted to add my two cents to nexx's rant two months ago. 

I need IE6+ to run on Lucid because my company's Employee Self-Service website requires it for me to submit work schedule requests, leave-of-absences, etc. from home, as well as to check my upcoming schedule, payroll, benefits status, etc. Other browsers with User Agent switchers to "impersonate" IE6 on Windows fail on that website as well. 

I tried installing IE6 using ies4linux on Wine 1.0, which worked with Wine 0.9, but broke after that. I tried Wine 1.2, then 1.3, running "FakeIE" which comes in Wine 1.2+, then installing IE6, and later IE7 using winetricks. In short every combination of Wine with every version of IE. Each browser worked as reported on AppsDB, except on my company's employee site, where it either hung, or errored out. The latest error was 

Upgrading Files...
Cannot create BCClient ClientHelper. SuperCAB not installed correctly. Error description = Automation server can't create object.

So, there you are... Some people have a REALLY legitimate need for this crappy IE6. Even Microsoft wants IE6 to go away, but there are too many large corporations that find it daunting to migrate their web facilities with such a massive user base to something better. My company has 600+ locations each with multiple workstations. I think most are still running Windows XP. They can't afford the across-the-board hardware or Windows 7 upgrades for all the locations in this economic climate.

BTW, re the above error, I do have CABextract installed. Others report the same error as well, even Windows users. Also, I added the corporate domain to IE Trusted sites, so that's not the issue either.

---

### Post by roman.novacek on 2010-09-26
Hi, I have tried wineprefixcreate from google picasa adding to PATH
PATH=$PATH:/opt/google/picasa/3.0/wine/bin
and it works.

---

### Post by BigTA78 on 2010-11-12
Have you tried using PlayOnLinux? It's in the standard repositories and installable through the Ubuntu Software Centre.
If you click "Add" once installed, IE6&7 are in there.

---

### Post by nexx on 2010-11-14
Thank you so much BigTA78, Playonlinux seems wonderful, I now have a working "internet explorer" 6 and 7 installed on ubuntu 10.10 plus safari.
To be able to install both I needed to upgrade playonlinux to the latest version as the one from the depots was not able to install the two versions, I had only ie7 at first. As usual my website [www.artimap.com](www.artimap.com) does not works on ie6 :(

---

### Post by oriver on 2010-12-01
open the file: */ies4linux-2.0.5/lib/install.sh* with a text editor (gedit).
replace *Wineprefixcreate*  with *wineboot*, save and close the file.
Then execute with: *./ies4linux*
you will find ie6 under your-home/bin folder
run with: *./ie6*

---

### Post by spiffymap on 2011-03-15
ln -s /usr/bin/winecfg wineprefixcreate
also works.

---

### Post by prscott1 on 2011-03-22
Great!  the symbolic link to winecfg did the trick for me.  Much appreciated!

---

### Post by simonf87 on 2011-07-27
```
sudo apt-get install wine1.0
```
did the trick for me on natty

---

