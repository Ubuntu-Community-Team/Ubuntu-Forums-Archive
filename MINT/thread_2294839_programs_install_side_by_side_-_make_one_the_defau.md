---
title: "programs install side by side - make one the default"
date: 2015-09-13
forum: MINT
---

### Post by Kevin McCready on 2015-09-13
I have two versions of the same program installed side by side. 

Sometimes right click menu comes up with both when I right click on a file. So I can chose which one I want to open the file with.
BUT I want to make the more recent one the default.  Even when I click on the properties tab on the right click menu and adjust the properties to the version I want, it still reverts to the wrong version when I open the file. So somehow in the guts of the system I have to make a change. I also tried 
xdg-mime default 'app'.desktop application/'filetype'
but that didn't work.
My system is
$ cat /etc/*release*
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=17.2
DISTRIB_CODENAME=rafaela
DISTRIB_DESCRIPTION="Linux Mint 17.2 Rafaela"
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
NAME="Ubuntu"
VERSION="14.04.3 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.3 LTS"

---

### Post by tgalati4 on 2015-09-13
Post the output of:

```
whereis nameofyourprogramthatyouinstalledtwoversionsof
```

---

### Post by monkeybrain20122 on 2015-09-13
How did you install two versions of the same program in the same system? I am intrigued. Did you install one in your /home like by downloading a binary or compiling? Not knowing the details I think you can probably change the name of one .desktop file, say, instead of foo, make it foo-xyz where xyz is the version then you will have different versions in the right click menu.

---

### Post by Kevin McCready on 2015-09-14
whereis libreoffice
libreoffice: /usr/bin/libreoffice /etc/libreoffice /usr/lib/libreoffice /usr/bin/X11/libreoffice /usr/local/bin/libreoffice5.0 /usr/share/libreoffice /usr/share/man/man1/libreoffice.1.gz

ta again [**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895")

I installed 5.0 by creating a temp folder on my desktop, extracting a .gz file and following the instructions in the readme

---

### Post by Bucky Ball on 2015-09-14
Please use code tags for terminal output. See the last link in my signature. Thanks.

> **Kevin McCready said:**
> I installed 5.0 by creating a temp folder on my desktop, extracting a .gz file and following the instructions in the readme

Any reason for this? Always best to use the version tested with your release in the official repositories. :)

---

### Post by monkeybrain20122 on 2015-09-14
Well where is LO5.0 installed to? What is in the tar ball you downloaded? IIRC it should contain a whole bunch of .deb files which means you have to install into your system to work (rather than binaries which don't require installing) But you can only install one version of LO system wide so either you haven't installed it, so your version is actually still 4.x.x or if you did, then it has overwritten the 4.x.x version. 

What is the output of 
```
libreoffice --version
```

---

### Post by monkeybrain20122 on 2015-09-14
BTW, if you want to upgrade LO, you can just use its ppa
[https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

---

### Post by Kevin McCready on 2015-09-14
Both versions are installed and I can run either one. 
```

 $ libreoffice --version
LibreOffice 4.4.3.2 40m0(Build:2)

```

---

### Post by Kevin McCready on 2015-09-14
[ATTACH=CONFIG]264410[/ATTACH]

---

### Post by Bucky Ball on 2015-09-14
Could you describe how you launch each? I presume one is in the menu and the other you need to launch from the terminal?

---

### Post by Kevin McCready on 2015-09-14
There is an icon for 5.0 on my desktop and I can launch that even though it comes up with a warning that "The desktop file "libreoffice5.0-writer.desktop" is in an insecure location and not marked as executable. If you do not trust this program, click Cancel. Exec=libreoffice5.0 --writer %U."

When I right click the desktop icon and check properties it says "libreoffice5.0-writer.desktop"  and the link target is "/opt/libreoffice5.0/share/xdg/writer.desktop". Under permissions it says the owner is root (that could be bad?) and under the launcher tab it says "libreoffice5.0 --writer %U"
 
Unfortunately the 4.2.. version is the default which is launched when I click on a file in the file manager, or type libreoffice in the terminal.

---

### Post by monkeybrain20122 on 2015-09-14
Well if you just want 5.0 then first remove the version you installed manually. I think you have installed a bunch of .debs so they should have entries in synaptic. Remove all of those (they should be all in the section "local or obsolete" where all your manually installed packages are) If there is no entry in synaptic simply remove the directory /opt/libreoffice5.0

```
sudo rm -r /opt/libreoffice5.0
```

Now add the LO ppa and run update

```

sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get upgrade
```

Then you will have only LO 5.0. Now delete the launcher icon on your desktop.


Both versions side by side. For the menu to pick up LO5.0 , its .desktop files have to be in either/usr/share/applications, /usr/local/share/applications or ~/.local/share/applications. If you want to keep both versions then copy all the .desktop files from /opt/libreoffice5.0/share/xdg to ~/.local/share/applications then change the owner to yourself, make them excutable. e,g

```
sudo cp /opt/libreoffice5.0/share/xdg/*.desktop ~/.local/share/applications
cd ~/.local/share/applications
sudo chown yourusername writer.desktop
chmod +x wtiter.desktop
```

Do the same with other .desktop files. You may have to change the program name entry in these .desktop files, open each with an editor and change the part after the equal sign in  "Name=" to something that explicitly mentions version 5.0 in order to be different from the one for LO 4.
  
After doing the above if you right click a file to choose default applications (not sure the details in your DE) there should be two icons, one for LO, one for LO5.0

Finally, delete the launcher icon on your Desktop. If you want it there, recopy the .desktop files for LO5 from ~/.local/share/applications to ~/Desktop (or you may be able to drag and drop, not sure about Mint's DE)

**Edited:** I am under the impression that Mint can use Ubuntu's ppas (except for the Debian edition of course) But I am not so sure on second thought. Some Mint users may be able to advise you on that.

---

