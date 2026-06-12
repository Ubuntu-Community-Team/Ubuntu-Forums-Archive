---
title: "Difficulties installing (multiple programs)"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by legendmaker on 2008-07-17
Alright, my friend recommended that I use compiz fusion, and I ran into a series of troubles when trying to download/install it.  Basically, I ended up at the end of this chain needing to install **7-zip**, and the 7za file [supposedly stand-alone executable] will not do anything that I can see.  If anybody has any ideas on what to try, please let me know.  

Part of my problem seems to be that I'm not quite understanding how to operate repositories just yet, which I was trying to use in order to download a program called banshee, which showed the best reviews on multiple sites that I visited.  

Another one of my problems was in downloading my video card driver, which is the said problem with my compiz installation.  When I went to download the version I thought that I needed, which was built for the i386 (architecture?) in rpm format, It came up as a audio/x-pn-realaudio-plugin-object, which totally doesn't make any sense to me.  anyways, I went to get the realplayer, and of course, it comes in a .bin format, so I went to get powerISO to undo that.  However, the PowerISO package comes in .tar.gz format which can be undone with 7zip.  So, that's where I'm stuck in the first paragraph.  

Again, if anyone has any ideas, please let me know.  I know that most people don't have integrated intel graphics cards to deal with but perhaps you might know what to do regardless.

---

### Post by Partyboi2 on 2008-07-18
If you are using gusty or hardy compiz-fusion is already installed by default. You can go to Appearance (System>Pref>Appearance) on the visual effects tab, select extra. To configure compiz you can install compizconfig-settings-manager package.
Open a terminal (Applications>accessories>Terminal) and type
```
sudo apt-get install compizconfig-settings-manager 
```and you can run it from the terminal by typing
```
ccsm
``` or by System>Pref>Advanced Desktop Effects Settings

To install banshee you can install it from the terminal by typing
```
 sudo apt-get install banshee
```or you can open up add/remove (Applications>add/remove) and searching for the program and installing it. Make sure that the "show" field next to the "search" is showing "All Available Applications"

To install realplayer, in a terminal change directory to where the downloaded file is, so if its on your Desktop type
```
cd ~/Desktop
``` then make the file excutable
```
chmod a+x RealPlayer11GOLD.bin
```then install it by typing
```
./RealPlayer11GOLD.bin
```and following the prompts.
[[COLOR=Blue]Here[/COLOR]]("http://monkeyblog.org/ubuntu/installing/") is a link that will explain how to install programs

---

### Post by fishbulb1022 on 2008-07-22
I had problems with compiz as well, but i was able to find this post [http://ubuntuforums.org/showthread.php?t=799070]("http://ubuntuforums.org/showthread.php?t=799070")
it helped so much, the guys been thanked like a thousand times. he wrote a program called compiz-check which shows exactly whats happening and what you need for compiz to work, its fantastic. 

I also had trouble with the .tar.gz files, this should work, if it doesn't here's the like where i got most of the info (although i tried to make it more basic because just from the site it took me like an hour) [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

ok,
1. anytime you download a .tar.gz or whatever, just save it to the desktop, its just easier.

2. extract the files by right clicking and hitting "extract here" which will extract it to the desktop.

3. open a terminal window by going to Applications>Accessories>Terminal

4. type "cd Desktop" and make sure to capitalize the D

5. now type "ls" (thats a lowercase LS just for clarity's sake)

6. this should give you a list of all the directories on the desktop, find the one you want, it should be the name of whatever program you're trying to install, but make sure you don't pick the .tar, you want the one you extracted, which will be the same thing without the extension. Highlight and copy the name.

7. Now type "cd" and paste what you just copied after it (remembering the space between cd and the file name)

8. Now type ./configure to automatically configure the program. if it stops in the middle and says it needs a package, copy the name of the package, go to the synaptic package manager (system>administration>synaptic package manager) and do a search for that package. anything that looks the same with -dev on the end is also necessary, get it to. once you've got everything checked, click apply.

9. now back in the terminal (if you closed it, you'll have to navigate back to the directory again, using steps 4-7) type ./configure again

10. repeat steps 8-9 until all the packages necessary have been installed and the configuration completes.

11. Now type "make" to compile the code

12, now "make install" to install it

I hope this helps, it should work, if it doesn't feel free to ask more questions and check out the link i gave you (you should also check the "Navigating the Terminal" link they have, it was really helpful)

---

