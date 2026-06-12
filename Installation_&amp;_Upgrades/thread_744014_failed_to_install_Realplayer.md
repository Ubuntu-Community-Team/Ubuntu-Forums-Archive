---
title: "failed to install Realplayer"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by kjman83 on 2008-04-03
I tried installing but failed. What's the problem?
What should I do?


kjman83@guiness:~/Desktop$ chmod a+x RealPlayer10GOLD\(2\).bin 
kjman83@guiness:~/Desktop$ sudo ./RealPlayer10GOLD\(2\).bin 
./RealPlayer10GOLD(2).bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
kjman83@guiness:~/Desktop$

---

### Post by kellemes on 2008-04-03
This will fix it.. I guess.
```
sudo apt-get install libstdc++5
```

---

### Post by rookie4evr on 2008-04-03
"sudo apt-get install libstdc++5"

is this the code to install real player ???????
or do we have to do anything else????

---

### Post by kellemes on 2008-04-03
> **rookie4evr said:**
> "sudo apt-get install libstdc++5"

is this the code to install real player ???????
or do we have to do anything else????

[https://help.ubuntu.com/community/RealPlayerInstallationMethods]("https://help.ubuntu.com/community/RealPlayerInstallationMethods")

---

### Post by warp99 on 2008-04-03
You can install mplayer and mozilla-mplayer to view the embedded realvideo, no need to install Realplayer. Just do the following:

```
sudo apt-get install mplayer mozilla-mplayer
```

You may need the W32 codec package that is available at medibuntu.org. This guide will show you how to add the repositories and get the extra codec packages:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Chappy7777 on 2008-04-03
Here's what I do and it has yet to not work. 

1) Go to [www.real.com/linux](www.real.com/linux)  and click the download button.
2) Place the download in your home folder.

3) Quit Firefox and open a Terminal window.

4) Make the real audio install file executable by typing: 
  chmod a+x RealPlayer10Gold.bin    press ENTER (be sure and have the spaces after chmod            and x.

  type: sudo ./RealPlayerGold.bin   press Enter

   You'll be prompted to press enter, do so.

5) When asked to complete the path to where you want to install Real Player,
  Type: /opt/RealPlayer   press enter

6) In the next window, to begin copying files, accept default by pressing ENTER

7)When asked wjether to aloow installer to configure systomwide symbolic links, type Y, and press ENTER

8) You will now be asked to specify the prefix for symbolic links, just press ENTER.

After a short time it will tell you it's finsihed installing. You'll be returned to prompt. You can now close the terminal window. You can delete the .bin file if you want.

Go to Applications, Sounds and Video, select Real Audio and go thru the setup wizard. 

To test if it worked, go to [www.npr.org](www.npr.org)   (Or anywhere else you know there is a Real Audio link).  Click the link. A small Firefox window will appear.  It will be asking you what it should do with the file. Default shoud be    Open With:/usr/share/realplay     if so. click OK.
Don't click the box saying do this everytime.

That should do it. Good luck. Kudos to Richard Grant's book. Ubuntu Linux for Non Geeks that I bought a few years ago.

---

### Post by playme123 on 2008-04-14
> **warp99 said:**
> You can install mplayer and mozilla-mplayer to view the embedded realvideo, no need to install Realplayer. Just do the following:

```
sudo apt-get install mplayer mozilla-mplayer
```

You may need the W32 codec package that is available at medibuntu.org. This guide will show you how to add the repositories and get the extra codec packages:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

your a star am finally able to listen to radio 1:KS:KS:KS

---

