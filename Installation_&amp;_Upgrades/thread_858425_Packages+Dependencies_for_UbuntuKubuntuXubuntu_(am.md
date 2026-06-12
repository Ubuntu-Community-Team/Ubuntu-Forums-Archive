---
title: "Packages+Dependencies for Ubuntu/Kubuntu/Xubuntu (amd64) July 2008"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by nucleuskore on 2008-07-13
Enabling multimedia and restricted formats in systems not connected to the internet can be a pain with any linux distro with a lot of dependency problems. This is more so a problem for people in smaller cities with slow dial up connections or worse, no internet access at all. Being primarily a OpenSuSE user, I started redistributing OSS rpms of select software with their dependencies as zip archives in the month of December last year, and usually release updates every month, time permitting.

The response has been fairly good. What I and many users realised that this helps not only those who do not have access to internet at home, but also regular users who want to set up their system quickly after a format, or set up multiple PCs, saving bandwidth.

I decided to start the same work for Ubuntu, Kubuntu and Xubuntu 8.04, and will be redistributing the packages and dependencies through AptOnCD. I have selected a few software which may be required on home PCs. This list is in no way complete, but just represents what I think may be the bare minimum one would like to have on a multimedia desktop PC.

I have compiled a collection of applications and their dependencies for Ubuntu/Kubuntu/Xubuntu 8.04 (amd64) for installation to PCs not connected to the internet and for quick multimedia setup.

Here is the updated list of applications

**Application list:**
htop
kchmviewer
evince (for Kubuntu only)
mplayer (for Xubuntu and Ubuntu)
kmplayer (for Kubuntu only)
mozilla-mplayer plugin (for Ubuntu and Xubuntu)
audacious
k3b
libk3b2-extracodecs
normalize-audio
sox
vcdimager
devede
audacity
avidemux
ffmpeg
ffmpegthumbnailer
transcode
ntfs-config
vlc
libdvdcss2
non-free-codecs
peazip
compizconfig-settings
wine
ubuntu-restricted (Ubuntu only)
kubuntu-restricted (Kubuntu only)
xubuntu-restricted (Xubuntu only)

**Warning: For Peazip installation see the end of this post !!!!**

[size=+1]Instructions:[/size]
1. Download this iso file
   [Mirror 1 - FTP Download](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-amd64-aptoncd-20080713-CD1.iso)
[Mirror 2 - Rapidshare](http://rapidshare.com/files/129679171/UbuKuXu-amd64-aptoncd-20080713-CD1.iso)

   md5sum f8324fd3ac9deb39625258b34063c1ca
   Size: 197.8 MB

2. Burn iso to a cd.**

[size=+1]*Ubuntu specific instructions:*[/size]
3. Insert cd, it will open in nautilus along with this prompt
   [img]http://img146.imageshack.us/img146/2990/89697775yf4.png[/img]
4. Click start package manager, when you do that you will be prompted for your password
   [img]http://img146.imageshack.us/img146/2655/68918326kr4.png[/img]

   Key in your password and press ENTER

5. Close the quick introduction dialog box
   [img]http://img146.imageshack.us/img146/8769/12mm8.png[/img]

6. Now you will see the Synaptic Package Manager. Click the serch button and search for each of the above applications for your distro. When you find them click and mark for installation.

   As you mark them you will see dependency warning dialog boxes, select mark
   [img]http://img175.imageshack.us/img175/1192/66639439hd2.png[/img]

   **Don't search and mark peazip. We have to install it manually later as it is a 32 bit application.**
   After marking all the above packages for install, click upgrade all button and click mark. Then, if you do not have an
   internet connection or do not wish to download anything search for the following

   flashplugin-nonfree
   msttcorefonts

   and unmark them so that they will not be installed.


7. Click Apply. The installation will proceed
[img]http://img175.imageshack.us/img175/8755/84836551os5.png[/img]

8. After everything is installed click Close
[img]http://img175.imageshack.us/img175/1381/45563161ib1.png[/img]


Enjoy your Ubuntu !


[size=+1]*Xubuntu specific instructions:*[/size]

3. Insert cd, it will open in Thunar along with this prompt
[img]http://img291.imageshack.us/img291/5707/01aq7.png" width="640" height="480"[/img]

4. Click start package manager, when you do that you will be prompted for your password
[img]http://img291.imageshack.us/img291/7646/02bj7.png[/img]

Key in your password and press ENTER

---

### Post by nucleuskore on 2008-07-13
5. CLose the quick introduction dialog box
[img]http://img183.imageshack.us/img183/6505/03ex5.png[/img]

6. Now you will see the Synaptic Package Manager. Click the search button and search for each of the applications listed
   above for your distro. When you find them click and mark for installation.
[img]http://img183.imageshack.us/img183/8321/04al4.png[/img]
[img]http://img183.imageshack.us/img183/4774/05of5.png[/img]
[img]http://img183.imageshack.us/img183/4529/06hz4.png[/img]

As you mark them you will see dependency warning dialog boxes, select mark
[img]http://img149.imageshack.us/img149/4043/07lb8.png[/img]

<b>Don't search and mark peazip. We have to install it manually later as it is a 32 bit application.</b>

If you do not have an internet connection or do not wish to download anything search for the following

      flashplugin-nonfree
      msttcorefonts

      and unmark them so that they will not be installed.

7. Click Apply. 

[img]http://img384.imageshack.us/img384/9788/08pz8.png[/img]
[img]http://img384.imageshack.us/img384/7209/09hu1.png[/img]The installation will proceed

[img]http://img329.imageshack.us/img329/3341/10ny7.png[/img]

---

### Post by nucleuskore on 2008-07-13
[img]http://img329.imageshack.us/img329/180/11cd1.png[/img]

8. After everything is installed click Close

[img]http://img329.imageshack.us/img329/2876/12rq4.png[/img]

Enjoy your Xubuntu !


Kubuntu specific instructions:
3. Insert cd, you will see a prompt onscreen
[img]http://img355.imageshack.us/img355/4436/01qf2.png[/img]

Select Open in new window; a new window opens as below
[img]http://img355.imageshack.us/img355/7472/02mt8.png[/img]

Minimise it.

4. Click start (KMenu) -> System -> Adept Manager, when you do that you will be prompted for your password

[img]http://img355.imageshack.us/img355/2131/03co9.png[/img]

Key in your password and press ENTER

5. Now you will see the Adept Package Manager.

[img]http://img370.imageshack.us/img370/8623/04md7.png[/img]

6. Click Adept -> Manage Repositories
[img]http://img106.imageshack.us/img106/4774/05sf2.png[/img]

7. You will see this
[img]http://img370.imageshack.us/img370/6748/06cy9.png[/img]

---

### Post by nucleuskore on 2008-07-13
8. Click on the,"Third-Party Software" tab, and click Add CD-ROM
[img]http://img106.imageshack.us/img106/1104/07ul3.png[/img]

You will see this dialog box
[img]http://img229.imageshack.us/img229/4417/08ir2.png[/img]

Insert the CD you made in step 2; the following gets added automatically
[img]http://img229.imageshack.us/img229/3874/09hb1.png[/img]

In the search box type and search for each of the applications listed above for your distro. When you find them right click and mark for installation.

[img]http://img410.imageshack.us/img410/3606/10sx4.png[/img]

**Don't search and mark peazip. We have to install it manually later as it is a 32 bit application.**

If you do not have an internet connection or do not wish to download anything search for the following

flashplugin-nonfree
msttcorefonts

and unmark them so that they will not be installed.

9. Click Apply. The installation will proceed
[img]http://img258.imageshack.us/img258/3558/11by3.png[/img]
[img]http://img258.imageshack.us/img258/183/12gl0.png[/img]

10. After everything is installed close adept

Enjoy your Kubuntu !

[size=+1]**Peazip Installation:**[/size]
Copy the file peazip_2.1.bin.LINUX.GTK2.i586-1.deb from the packages folder in the cd to your home folder
Open a terminal (Applications->Accessories->Terminal)
Type the following command

sudo dpkg -i --force architecture peazip_2.1.bin.LINUX.GTK2.i586-1.deb

and press ENTER

[img]http://img244.imageshack.us/img244/2448/peazipav9.png[/img]

Peazip will be installed.
To run Peazip click on Applications->System->Peazip

---

### Post by nucleuskore on 2008-09-02
Hi all
I have modified this release a little. No I've included two ISOs
[list=1]
[*]only multimedia packages
[*] multimedia packages + default system updates[/list]

So you can download whichever suits your needs the best :)

**Application list (September 2008):**

**htop** - an extension of top for viewing system processes

**kchmviewer** - a CHM viewer

**evince** (for Kubuntu only) - a pdf viewer

**mplayer** - a multimedia player

**kmplayer (for Kubuntu only)** - instead of Mplayer. If you install firefox then do install mozilla-mplayer

**firefox**(for Kubuntu only as it does not have firefox)

**mozilla-mplayer plugin** - Mplayer plugin for firefox

**audacious** - a winamp look-alike

**k3b** - burn baby burn, CD/DVD burning

**libk3b2-extracodecs** - extra codecs for K3b

**normalize-audio** - needed for K3b

**sox** - needed for K3b

**vcdimager** - needed for K3b

**devede** - DVD authoring

**audacity** - sound file editor

**avidemux** - A demuxer, similar to VirtualDub

**ffmpeg** - CLI video encoder

**ffmpegthumbnailer** - make thumbnails of your movies like in Media Player Classic of Klite

**transcode** - CLI video encoder

**ntfs-config** - Easy configuration to mount and write to internal/external ntfs drives

**vlc** - multimedia player

**libdvdcss2** - dvd decryptor

**non-free-codecs** - required for Mplayer and Kaffeine

**wine** - a Windows emulator

**ubuntu-restricted (Ubuntu only)**

**kubuntu-restricted (Kubuntu only)** 

**xubuntu-restricted (Xubuntu only)** 

I forgot to include Peazip. Please see the end of this post.

**Instructions:**

[list]

  [*]Download one of these iso files
    [list]

      [*]Packages listed above **without** default system upgrade

[FTP Download](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-aptoncd-20080902_amd64-CD1.iso) md5sum 6ae43b1f122a8f2f483dcce8c7012eeb

[*]Packages listed above **with** default system upgrade

I have split this iso into six peices to facilitate easy download.
Mediafire.com supports download managers so don't worry.

[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca2b345e56fab4457b](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca2b345e56fab4457b)
        
[/list]

We are now going to use a terminal to assemble the file. Do not be afraid, the command line is your friend !
**Tip:** when you are keying in the name of a file in the current folder that you are in, just type the partial name and press the Tab key once; if the file name is unique it will autocomplete

Press Alt and F2, and type

gnome-terminal (in Ubuntu)

konsole (in Kubuntu)

xterm (in Xubuntu)

By default you will now be in your home folder. We now want to navigate to the desktop where you saved your downloaded files.


Type

cd Desktop

and press ENTER.

Note that the D of Desktop is in capitals. Linux is case sensitive -
Desktop is not the same as desktop


Type

ls

and press ENTER.

You should see the six files, 02092008_aa to 02092008_af, besides other files if any on your desktop.


Type

md5sum 02092008_a*

and press ENTER. You should see the following output

b2469fba0b5a4c1a674f399a08b9d026  02092008_aa
746c350f7b9a6f2f604282b152abb35a  02092008_ab
32450fac7f5740e145b9b95192ca2d51  02092008_ac
0a300ae78f1a8017d6656f5dc481ac25  02092008_ad
757d28adbcbad27c12f19e4c16c7fa1f  02092008_ae
4614afd7f711fbcc0b4acab6fa11898a  02092008_af

that is, the md5sum with the corresponding filename.

This means your files are ok, if any of them differ then that particular part file has got corrupted during download and will have to be redownloaded.


If all is well, type

cat 02092008_a* > upgrade.iso

and press ENTER. 

Wait till you get the prompt back, the file upgrade.iso will be assembled on your desktop.


Type

ls

and press ENTER.

You should see the file upgrade.iso among other files on your desktop.


You can now write it to a cd using the default cd burning software of your distro.

  [*]Burn iso to a cd

***Ubuntu specific instructions:***
    
[*]Insert cd, it will open in nautilus along with this
prompt
    
[[img]http://img146.imageshack.us/img146/2990/89697775yf4.th.png[/img]](http://img146.imageshack.us/my.php?image=89697775yf4.png) 

[*]Click start package manager, when you do that you will be prompted for your password

[[img]http://img146.imageshack.us/img146/2655/68918326kr4.th.png[/img]](http://img146.imageshack.us/my.php?image=68918326kr4.png)

Key in your password and press ENTER

[*]CLose the quick introduction dialog box

[[img]http://img146.imageshack.us/img146/8769/12mm8.th.png[/img]](http://img146.imageshack.us/my.php?image=12mm8.png)

[*]Now you will see the Synaptic Package Manager. Click the search button and search for each of the above applications for your distro. When you find them click and mark for installation.

As you mark them you will see dependency warning dialog boxes, select mark

[[img]http://img175.imageshack.us/img175/1192/66639439hd2.th.png[/img]](http://img175.imageshack.us/my.php?image=66639439hd2.png)

If you downloaded the upgrade iso, after marking all the above packages for install, click upgrade all button and click mark. 
[b]Then, if you do not have an internet connection or do not wish to download anything search for the following

flashplugin-nonfree
msttcorefonts

and unmark them so that they will not be installed.[/b]

[*]Click Apply. The installation will proceed

[[img]http://img175.imageshack.us/img175/8755/84836551os5.th.png[/img]](http://img175.imageshack.us/my.php?image=84836551os5.png)

8. After everything is installed click Close

[[img]http://img175.imageshack.us/img175/1381/45563161ib1.th.png[/img]](href="http://img175.imageshack.us/my.php?image=45563161ib1.png)

[/list]

Enjoy your Ubuntu !

---

### Post by nucleuskore on 2008-09-02
***Xubuntu specific instructions:***
[list=3]

  [*]Insert cd, it will open in Thunar along with this prompt

[[img]http://img291.imageshack.us/img291/5707/01aq7.th.png[/img]](http://img291.imageshack.us/my.php?image=01aq7.png)  

  [*]Click start package manager, when you do that you will be prompted for your password

[[img]http://img291.imageshack.us/img291/7646/02bj7.th.png[/img]](http://img291.imageshack.us/my.php?image=02bj7.png)

Key in your password and press ENTER

[*]CLose the quick introduction dialog box

[[img]http://img183.imageshack.us/img183/6505/03ex5.th.png[/img]](http://img183.imageshack.us/my.php?image=03ex5.png)

[*]Now you will see the Synaptic Package Manager. Click the
search button and search for each of the applications listed above for
your distro. When you find them click and mark for installation.

[[img]http://img183.imageshack.us/img183/8321/04al4.th.png[/img]](http://img183.imageshack.us/my.php?image=04al4.png)[[img]http://img183.imageshack.us/img183/4774/05of5.th.png[/img]](http://img183.imageshack.us/my.php?image=05of5.png)[[img]http://img183.imageshack.us/img183/4529/06hz4.th.png[/img]](href="http://img183.imageshack.us/my.php?image=06hz4.png)

As you mark them you will see dependency warning dialog boxes, select mark

[[img]http://img149.imageshack.us/img149/4043/07lb8.th.png[/img]](http://img149.imageshack.us/my.php?image=07lb8.png)

If you downloaded the upgrade iso, after marking all the above packages for install, click upgrade all button and click mark. [b]Then, if you do not have an internet connection or do not wish to download anything search for the following 

flashplugin-nonfree
msttcorefonts

and unmark them so that they will not be installed.[/b]

---

### Post by nucleuskore on 2008-09-02
[*]Click Apply. The installation will proceed

[[img]http://img384.imageshack.us/img384/9788/08pz8.th.png[/img]](href="http://img384.imageshack.us/my.php?image=08pz8.png)[[img]http://img384.imageshack.us/img384/7209/09hu1.th.png[/img]](http://img384.imageshack.us/my.php?image=09hu1.png)[[img]http://img329.imageshack.us/img329/3341/10ny7.th.png[/img]](http://img329.imageshack.us/my.php?image=10ny7.png)[[img]http://img329.imageshack.us/img329/180/11cd1.th.png[/img]](http://img329.imageshack.us/my.php?image=11cd1.png)

[*]After everything is installed click Close

[[img]http://img329.imageshack.us/img329/2876/12rq4.th.png[/img]](http://img329.imageshack.us/my.php?image=12rq4.png)  

[/list]

Enjoy your Xubuntu !

<hr>


***Kubuntu specific instructions:***
[list=3]

[*]Insert cd, you will see a prompt onscreen

[[img]http://img355.imageshack.us/img355/4436/01qf2.th.png[/img]](http://img355.imageshack.us/my.php?image=01qf2.png)    

Select Open in new window; a new window opens as below

[[img]http://img355.imageshack.us/img355/7472/02mt8.th.png[/img]](http://img355.imageshack.us/my.php?image=02mt8.png)    

Minimise it.

[*]Click start (KMenu)->System->Adept Manager, when you do that you will be prompted for your password

[[img]http://img355.imageshack.us/img355/2131/03co9.th.png[/img]](http://img355.imageshack.us/my.php?image=03co9.png)

Key in your password and press ENTER

---

### Post by nucleuskore on 2008-09-02
[*]Now you will see the Adept Package Manager. 

[[img]http://img370.imageshack.us/img370/8623/04md7.th.png[/img]](http://img370.imageshack.us/my.php?image=04md7.png)

[*]Click Adept -&gt; Manage Repositories

[[img]http://img106.imageshack.us/img106/4774/05sf2.th.png[/img]](http://img106.imageshack.us/my.php?image=05sf2.png)  

[*]You will see this

[[img]http://img370.imageshack.us/img370/6748/06cy9.th.png[/img]](http://img370.imageshack.us/my.php?image=06cy9.png)

[*] Click on the,"Third-Party Software" tab, and click Add CD-ROM

[[img]http://img106.imageshack.us/img106/1104/07ul3.th.png[/img]](http://img106.imageshack.us/my.php?image=07ul3.png)    

You will see this dialog box

[[img]http://img229.imageshack.us/img229/4417/08ir2.th.png[/img]](http://img229.imageshack.us/my.php?image=08ir2.png)

Insert the CD you made in step 2; the following gets added automatically

[[img]http://img229.imageshack.us/img229/3874/09hb1.th.png[/img]](href="http://img229.imageshack.us/my.php?image=09hb1.png)

In the search box type and search for each of the applications listed above for your distro. When you find them right click and mark for installation.

[[img]http://img410.imageshack.us/img410/3606/10sx4.th.png[/img]](http://img410.imageshack.us/my.php?image=10sx4.png)

If you downloaded Upgrade_UbuKuXu-aptoncd-20080729-CD1.iso, after marking all the above packages for install, click upgrade all button and click mark. [b]Then, if you do not have an internet connection or do not wish to download anything search for the following

flashplugin-nonfree
msttcorefonts

and unmark them so that they will not be installed.[/b]

---

### Post by nucleuskore on 2008-09-02
[*] Click Apply Changes. The installation will proceed

[[img]http://img258.imageshack.us/img258/3558/11by3.th.png[/img]](http://img258.imageshack.us/my.php?image=11by3.png)[[img]http://img258.imageshack.us/img258/183/12gl0.th.png[/img]](http://img258.imageshack.us/my.php?image=12gl0.png)

[*]After everything is installed close adept

[/list]

Enjoy your Kubuntu !

--------------------------------------------------------------------------------------------------------------------
Peazip Installation:

    * Dowload the Peazip installer (deb) from [http://peazip.sourceforge.net](http://peazip.sourceforge.net) to your home folder
    * Open a terminal (Applications->Accessories->Terminal)
    * Type the following command

      sudo dpkg -i --force architecture peazip_2.1.bin.LINUX.GTK2.i586-1.deb

      and press ENTER

---

### Post by nucleuskore on 2008-10-04
Hi everyone
Here is the update for the month of October.

**Multimedia packages only** (as listed in above post) - not released as nothing significant was updated. Last month's download link is still active.

**Multimedia packages + Complete system update**

[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca6bab116e340223b0](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca6bab116e340223b0)

Download the six files and assemble and install as described above. 

32aaf0a765f2ccb01c88e027eba38d75   amd64_03102008_aa
ba62bc06218d957f36cefa073599d15d   amd64_03102008_ab
2dea76fed869ea8c8b3bab6e3fb9a9a2   amd64_03102008_ac
5a7dc6896fa8a8317a7cb0826f746457   amd64_03102008_ad
235598cbd46f5243a467ab0ee89a425a   amd64_03102008_ae
65de191e05878e9e9a598216078feb0c   amd64_03102008_af

---

### Post by nucleuskore on 2008-12-10
Hi everyone
Here is the update for the month of December, 2008.

Multimedia packages only (as listed in above post)

For 8.04: [ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.04-64bit-small-aptoncd-20081208-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.04-64bit-small-aptoncd-20081208-CD1.iso)
md5sum 758915ccd92a5b5bcd9bb1ace81af930

For 8.10: [ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.10-64bit-small-aptoncd-20081209-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.10-64bit-small-aptoncd-20081209-CD1.iso) 
ac1c8ae8a6022ddf3eb2d4ebfc759b8b


Multimedia packages + Complete system update

For 8.04: [http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d243d3ec96dfac810d](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d243d3ec96dfac810d)

For 8.10: [http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d2e0d84989e24b79f8](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d2e0d84989e24b79f8)

md5sums mentioned against each file.

md5sums of assembled ISOs
6f7a7d2fbd7c78c130fa3eb411893a9cfor 8.04
281fea5e04c394e026ddda5f591c60b8 for 8.10

Install instructions: See [http://ubuntuforums.org/showthread.php?t=858425#5](http://ubuntuforums.org/showthread.php?t=858425#5)

Note: Kubuntu 8.10 seems to have a problem with the Adept manager, I could not find an upgrade all button. So What you can do is first install the above packages, and then close adept and open a konsole and type

sudo apt-get upgrade

and press ENTER

---

### Post by nucleuskore on 2009-01-08
Hi everyone
Here is the update for the month of January, 2009.

Multimedia packages only (as listed in above post)

For 8.04: [ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.04-small-64bit-aptoncd-20090104-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.04-small-64bit-aptoncd-20090104-CD1.iso)
md5sum abdb402f45d5923d98450b237c815016

For 8.10: [ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.10-small-64bit-aptoncd-20090105-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.10-small-64bit-aptoncd-20090105-CD1.iso) 
md5sum 9c7ffcd1e001870d7d0a74ad5c7b5c0e


Multimedia packages + Complete system update

For 8.04: [http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d2438ccbf44940f2a4](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d2438ccbf44940f2a4)

For 8.10: [http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d254c5cea7574735cf](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d254c5cea7574735cf)

md5sums mentioned against each file below:

8.04
8a2ea22747275371dfb9cf24415a0325  aa
7c0eada3a0f47eff75a153869c8770aa  ab
d55b95181830ddca4f42ba9c4df28387  ac
32da475d27fcabb5fbfa279a7b908ed6  ad
2ed654eb1c750a8d704387c716d69975  ae
0af3c128210fd35af84b52a5353e1743  af
552d447f9708c7f52bb12c1274c88664  ag

8.10
71aabb62f9db9069184389c7ba4e5203  aa
27f19dc0ae93e177420dbb161f9bef8d  ab
8111c7a5a7c4d6952057663dabd9c689  ac
75d6260e7eba0380ac72ae95c70a03b0  ad
e4f960c8623806f50bbe9e0b8bc460ae  ae
5fc94cd411cbca6d38b2d9901355ee41  af

md5sums of assembled ISOs
5a4b37992a8c0dd62552088b70b94d3a for 8.04
393334390447cbdbbc390b4e1ec4dd9b for 8.10

Install instructions: See [http://ubuntuforums.org/showthread.php?t=858425#5](http://ubuntuforums.org/showthread.php?t=858425#5)

Note: Kubuntu 8.10 seems to have a problem with the Adept manager, I could not find an upgrade all button. So What you can do is first install the above packages, and then close adept and open a konsole and type

sudo apt-get upgrade

and press ENTER

---

### Post by nucleuskore on 2009-04-17
Hi everyone
Here is the update for the month of January, 2009.

Multimedia packages only (as listed in above post)

For 8.04: [ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.04-small-64bit-aptoncd-20090415-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.04-small-64bit-aptoncd-20090415-CD1.iso)
md5sum 07cda3336e0c7e4c2b16a8b5e793a66f

For 8.10: [ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.10-small-64bit-aptoncd-20090412-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.10-small-64bit-aptoncd-20090412-CD1.iso) 
md5sum 8cb4977a3b77e829e0e1decfdd27aa4b

Multimedia packages + Complete system update

For 8.04: [http://www.mediafire.com?sharekey=8b50ec8c0aafc4e87069484bded33bcd94790443316aaaa3](http://www.mediafire.com?sharekey=8b50ec8c0aafc4e87069484bded33bcd94790443316aaaa3)

For 8.10: [http://www.mediafire.com?sharekey=8b50ec8c0aafc4e87069484bded33bcdac622ff3f43e9748](http://www.mediafire.com?sharekey=8b50ec8c0aafc4e87069484bded33bcdac622ff3f43e9748)

md5sums mentioned against each file.

md5sums of assembled ISOs
96774fdc9ed205c28a694ccc9f45c877 for 8.04
08f5695d11138da631383e1d543ba1c4 for 8.10

Install instructions: See [http://ubuntuforums.org/showthread.php?t=858425#5](http://ubuntuforums.org/showthread.php?t=858425#5)

Note: Kubuntu 8.10 seems to have a problem with the Adept manager, I could not find an upgrade all button. So What you can do is first install the above packages, and then close adept and open a konsole and type

sudo apt-get upgrade

and press ENTER

---

### Post by nucleuskore on 2009-04-19
^Updated

---

### Post by nucleuskore on 2009-05-05
Packages for Jaunty Jackalope. Includes two new packages, mozplugger and timidity.

[http://massmirror.com/6f10764185964459f9bdc6b6784259a0.html](http://massmirror.com/6f10764185964459f9bdc6b6784259a0.html)

---

### Post by nucleuskore on 2009-07-08
Hi everyone
Here is the update for the month of July, 2009. From this release onwards, both small and large isos of the current stable release (currently Jaunty) will be uploaded to the ftp server.

Application list:
[list=1]
[*]**htop** - an extension of top for viewing system processes
[*]**kchmviewer** - a CHM viewer
[*]**evince** (for Kubuntu only) - a pdf viewer
[*]**mplayer** - a multimedia player
[*]**kmplayer** (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]**firefox**(for Kubuntu only as it does not have firefox)
[*]**mozilla-mplayer** plugin - Mplayer plugin for firefox
[*]**audacious** - a winamp look-alike
[*]**k3b** - burn baby burn, CD/DVD burning
[*]**libk3b2-extracodecs** - extra codecs for K3b
[*]**normalize-audio** - needed for K3b
[*]**sox** - needed for K3b
[*]**vcdimager** - needed for K3b
[*]**devede** - DVD authoring
[*]**audacity** - sound file editor
[*]**avidemux** - A demuxer, similar to VirtualDub
[*]**ffmpeg** - CLI video encoder
[*]**ffmpegthumbnailer** - make thumbnails of your movies like in Media Player Classic of Klite
[*]**transcode** - CLI video encoder
[*]**ntfs-config** - Easy configuration to mount and write to internal/external ntfs drives
[*]**vlc** - multimedia player
[*]**libdvdcss2** - dvd decryptor
[*]**non-free-codecs** - required for Mplayer and Kaffeine
[*]**libxine1** - for Kubuntu only
[*]**kaffeine** - for Kubuntu only
[*]**wine** - a Windows emulator
[*]**ubuntu-restricted-extras** (Ubuntu only)
[*]**kubuntu-restricted-extras** (Kubuntu only)
[*]**xubuntu-restricted-extras** (Xubuntu only)[/list]

Multimedia packages only (as listed in above post)

For 8.04: []()
md5sum 

For 8.10: [http://www.zshare.net/download/62417334333f5e02/](http://www.zshare.net/download/62417334333f5e02/) 
md5sum 3fd07e3e6ce22c17f75e727a817a5fbd

For 9.04: [ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/Ubuntu-9.04-64bit-July2009-small-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/Ubuntu-9.04-64bit-July2009-small-CD1.iso)
md5sum a23f39b40f6d954f223f12acae97c932

Multimedia packages + Complete system update

For 8.04: []()

For 8.10: [http://www.zshare.net/download/6244177632f344ce/](http://www.zshare.net/download/6244177632f344ce/)
3a4bf98d0d66d94245e5ea8a469bd799

For 9.04: [ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/Ubuntu-9.04-64bit-July2009-large-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/Ubuntu-9.04-64bit-July2009-large-CD1.iso)
md5sum f259522ea3ca87c58c8be72744b95a3c

Install instructions: See [http://ubuntuforums.org/showthread.php?t=858425#5](http://ubuntuforums.org/showthread.php?t=858425#5)

Note: Kubuntu 8.10 seems to have a problem with the Adept manager, I could not find an upgrade all button. So What you can do is first install the above packages, and then close adept and open a konsole and type

sudo apt-get upgrade

and press ENTER

---

### Post by nucleuskore on 2009-12-02
Hi everybody :(

Was in a transition phase, moving from India to Antigua. That's why I was not to be seen. Yes, I am in Antigua ! Land of sea and sun as they say. Am working for the American University of Antigua. Hope to be updating my packages threads regularly from January next year.

Am still trying to get my broadband connection here. I got the router day before yesterday from APUA, and they told me that it will take another four days to activate the line :-P
And unlike in India, they just give you your boxed new configured router, and a sheet of instructions on how to connect it to your PC. No tech guy come to your place like they do in India.

So till I get a proper broadband connection all my work is shelved.

On a brighter note I am going to get married soon. Will be arriving in India on the 14th of December :)

More on that here
[http://www.alovelycouple.co.cc](http://www.alovelycouple.co.cc)

---

### Post by The Bright Side on 2009-12-02
Congratulations!!

---

### Post by nucleuskore on 2009-12-11
Hi
Here is the a list of applications. I will be releasing the iso for 9.10 only, due to bandwidth constraints 

Application list (December 2009)
[list]
[*]htop - an extension of top for viewing system processes
[*]kchmviewer - a CHM viewer
[*]evince (for Kubuntu only) - a pdf viewer
[*]mplayer - a multimedia player
[*]kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]firefox(for Kubuntu only as it does not have firefox)
[*]mozilla-mplayer plugin - Mplayer plugin for firefox
[*]audacious - a winamp look-alike
[*]k3b - burn baby burn, CD/DVD burning
[*]libk3b6-extracodecs - extra codecs for K3b
[*]normalize-audio - needed for K3b
[*]sox - needed for K3b
[*]vcdimager - needed for K3b
[*]devede - DVD authoring
[*]audacity - sound file editor
[*]avidemux - A demuxer, similar to VirtualDub
[*]ffmpeg - CLI video encoder
[*]ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite
[*]transcode - CLI video encoder
[*]ntfs-config - Easy configuration to mount and write to internal/external [*]ntfs drives
[*]vlc - multimedia player
[*]libdvdcss2 - dvd decryptor
[*]libxine1 - for Kubuntu only
[*]kaffeine - for Kubuntu only
[*]w64codecs - required for Mplayer and Kaffeine
[*]wine - a Windows emulator
[*]ttf-liberation
[*]libavformat-extra-52
[*]libpostproc-extra-51
[*]libswscale-extra-0
[*]ubuntu-restricted (Ubuntu only)
[*]kubuntu-restricted (Kubuntu only)
[*]xubuntu-restricted (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade -

[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-9.10-64bit-aptoncd-20091207-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-9.10-64bit-aptoncd-20091207-CD1.iso)
 

Deployment: See [http://ubuntuforums.org/showthread.php?t=858425#5](http://ubuntuforums.org/showthread.php?t=858425#5)

---

### Post by nucleuskore on 2010-01-15
Hi
Here is the a list of applications for 9.10 only

Application list (January 2010)
[list]
[*]htop - an extension of top for viewing system processes
[*]kchmviewer - a CHM viewer
[*]evince (for Kubuntu only) - a pdf viewer
[*]mplayer - a multimedia player
[*]kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]firefox(for Kubuntu only as it does not have firefox)
[*]mozilla-mplayer plugin - Mplayer plugin for firefox
[*]audacious - a winamp look-alike
[*]k3b - burn baby burn, CD/DVD burning
[*]libk3b6-extracodecs - extra codecs for K3b
[*]normalize-audio - needed for K3b
[*]sox - needed for K3b
[*]vcdimager - needed for K3b
[*]devede - DVD authoring
[*]audacity - sound file editor
[*]avidemux - A demuxer, similar to VirtualDub
[*]ffmpeg - CLI video encoder
[*]ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite
[*]transcode - CLI video encoder
[*]ntfs-config - Easy configuration to mount and write to internal/external [*]ntfs drives
[*]vlc - multimedia player
[*]libdvdcss2 - dvd decryptor
[*]libxine1 - for Kubuntu only
[*]kaffeine - for Kubuntu only
[*]w64codecs - required for Mplayer and Kaffeine
[*]wine - a Windows emulator
[*]ttf-liberation
[*]libavformat-extra-52
[*]libpostproc-extra-51
[*]libswscale-extra-0
[*]ubuntu-restricted (Ubuntu only)
[*]kubuntu-restricted (Kubuntu only)
[*]xubuntu-restricted (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade.
Download the following parts to your home folder.

md5sum 6b4146b3a990fb3aa04710631831d10d  
[http://rapidshare.com/files/335730764/64_large_aa](http://rapidshare.com/files/335730764/64_large_aa)

md5sum d1878b59e8eb84bc0939bbfd3faaa365
[http://rapidshare.com/files/335730769/64_large_ab](http://rapidshare.com/files/335730769/64_large_ab)

md5sum 0a8734b1acfc5b75380aa56387ea49fe
[http://rapidshare.com/files/335733176/64_large_ac](http://rapidshare.com/files/335733176/64_large_ac)

md5sum fecf542c09ab4f69d5fe04be096d5aec
[http://rapidshare.com/files/335733181/64_large_ad](http://rapidshare.com/files/335733181/64_large_ad)

md5sum fac4a1579940985d7e9c7a5630a15aab
[http://rapidshare.com/files/335781129/64_large_ae](http://rapidshare.com/files/335781129/64_large_ae)

md5sum 210df8bda2b54365e9f316fc1e38db11
[http://rapidshare.com/files/335781131/64_large_af](http://rapidshare.com/files/335781131/64_large_af)

**Alternatively, download all the above pieces from here** (download manager supported)
[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca195ebe99d44afe08](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca195ebe99d44afe08)

To join the above, open a terminal (Press Alt and F2 and type gnome-terminal in Ubuntu, or konsole in Kubuntu, and press ENTER) and type

cat large_a* > large.iso

Burn the large.iso to a cd.
 
Deployment: See [http://ubuntuforums.org/showthread.php?t=858425#5](http://ubuntuforums.org/showthread.php?t=858425#5)

---

### Post by nucleuskore on 2010-03-29
Hi
Here is the a list of applications for 9.10 only

Application list (March 2010)
[list]
[*]htop - an extension of top for viewing system processes
[*]kchmviewer - a CHM viewer
[*]evince (for Kubuntu only) - a pdf viewer
[*]mplayer - a multimedia player
[*]kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]firefox(for Kubuntu only as it does not have firefox)
[*]mozilla-mplayer plugin - Mplayer plugin for firefox
[*]audacious - a winamp look-alike
[*]k3b - burn baby burn, CD/DVD burning
[*]libk3b6-extracodecs - extra codecs for K3b
[*]normalize-audio - needed for K3b
[*]sox - needed for K3b
[*]vcdimager - needed for K3b
[*]devede - DVD authoring
[*]audacity - sound file editor
[*]avidemux - A demuxer, similar to VirtualDub
[*]ffmpeg - CLI video encoder
[*]ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite
[*]transcode - CLI video encoder
[*]ntfs-config - Easy configuration to mount and write to internal/external [*]ntfs drives
[*]vlc - multimedia player
[*]libdvdcss2 - dvd decryptor
[*]libxine1 - for Kubuntu only
[*]kaffeine - for Kubuntu only
[*]w64codecs - required for Mplayer and Kaffeine
[*]wine - a Windows emulator
[*]ttf-liberation
[*]libavformat-extra-52
[*]libpostproc-extra-51
[*]libswscale-extra-0
[*]ubuntu-restricted (Ubuntu only)
[*]kubuntu-restricted (Kubuntu only)
[*]xubuntu-restricted (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade.

Download the iso from here (Fast FTP link)
[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-9.10-64bit-aptoncd-20100329-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-9.10-64bit-aptoncd-20100329-CD1.iso)

Burn the iso to a cd.
 
Deployment: See [http://ubuntuforums.org/showthread.php?t=858425#5](http://ubuntuforums.org/showthread.php?t=858425#5)

---

### Post by nucleuskore on 2010-05-19
Hi
Here is the a list of applications for 10.04 (lucid) only

Application list (May 2010)
[list]
[*]**htop** - an extension of top for viewing system processes
[*]**kchmviewer** - a CHM viewer
[*]**mplayer** - a multimedia player
[*]**gecko-mediaplayer** - a plugin for firefox to handle multimedia
[*]**timidity** - midi player
[*]**mozplugger** - optional but recommended plugin for firefox to handle multimedia
[*]**gimp** - Image editing
[*]**gimp-help-en** - english help file for GIMP, can be skipped
[*]**gimp-data-extras** - install with gimp above
[*]**firefox**(for Kubuntu only as it does not have firefox)
[*]**audacious** - a winamp look-alike
[*]**k3b** - burn baby burn, CD/DVD burning
[*]**libk3b6-extracodecs** - extra codecs for K3b
[*]**normalize-audio** - needed for K3b
[*]**sox** - needed for K3b
[*]**vcdimager** - needed for K3b
[*]**devede** - DVD authoring
[*]**audacity** - sound file editor
[*]**avidemux** - A demuxer, similar to VirtualDub
[*]**ffmpeg** - CLI video encoder
[*]**ffmpegthumbnailer** - make thumbnails of your movies like in Media Player Classic of Klite
[*]**transcode** - CLI video encoder
[*]**vlc** - multimedia player
[*]**libdvdcss2** - dvd decryptor
[*]**wine** - a Windows emulator
[*]**ttf-liberation**
[*]**libavformat-extra-52**
[*]**libpostproc-extra-51**
[*]**libswscale-extra-0**
[*]**ubuntu-restricted-extras** (Ubuntu only)
[*]**kubuntu-restricted-extras** (Kubuntu only)
[*]**xubuntu-restricted-extras** (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade.

Download the iso from here (Fast FTP link)
[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.04-64bit-aptoncd-20100518-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.04-64bit-aptoncd-20100518-CD1.iso)

Burn the iso to a cd.
 
Deployment: See [http://ubuntuforums.org/showthread.php?t=858425#5](http://ubuntuforums.org/showthread.php?t=858425#5)

---

### Post by nucleuskore on 2010-11-02
Hi
Here is the a list of applications for 10.10 only

Application list (November 2010)
[list]
[*]**htop** - an extension of top for viewing system processes
[*]**kchmviewer** - a CHM viewer
[*]**mplayer** - a multimedia player
[*]**gecko-mediaplayer** - a plugin for firefox to handle multimedia
[*]**timidity** - midi player
[*]**mozplugger** - optional but recommended plugin for firefox to handle multimedia
[*]**gimp** - Image editing
[*]**gimp-help-en** - english help file for GIMP, can be skipped
[*]**gimp-data-extras** - install with gimp above
[*]**firefox**(for Kubuntu only as it does not have firefox)
[*]**audacious** - a winamp look-alike
[*]**k3b** - burn baby burn, CD/DVD burning
[*]**libk3b6-extracodecs** - extra codecs for K3b
[*]**normalize-audio** - needed for K3b
[*]**sox** - needed for K3b
[*]**vcdimager** - needed for K3b
[*]**devede** - DVD authoring
[*]**audacity** - sound file editor
[*]**avidemux** - A demuxer, similar to VirtualDub
[*]**ffmpeg** - CLI video encoder
[*]**ffmpegthumbnailer** - make thumbnails of your movies like in Media Player Classic of Klite
[*]**transcode** - CLI video encoder
[*]**vlc** - multimedia player
[*]**libdvdcss2** - dvd decryptor
[*]**wine** - a Windows emulator
[*]**ttf-liberation**
[*]**libavformat-extra-52**
[*]**libpostproc-extra-51**
[*]**libswscale-extra-0**
[*]**ubuntu-restricted-extras** (Ubuntu only)
[*]**kubuntu-restricted-extras** (Kubuntu only)
[*]**xubuntu-restricted-extras** (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade.

Download the iso from here (Fast FTP link)
[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.10-amd64-aptoncd-20101102-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.10-amd64-aptoncd-20101102-CD1.iso)

Burn the iso to a cd.
 
Deployment: See [http://ubuntuforums.org/showthread.php?t=858425#5](http://ubuntuforums.org/showthread.php?t=858425#5)

---

### Post by nucleuskore on 2011-02-04
Hi
Here is the a list of applications for 10.10 only

Application list (February 2011)
[list]
[*]**htop** - an extension of top for viewing system processes
[*]**kchmviewer** - a CHM viewer
[*]**mplayer** - a multimedia player
[*]**gecko-mediaplayer** - a plugin for firefox to handle multimedia
[*]**timidity** - midi player
[*]**mozplugger** - optional but recommended plugin for firefox to handle multimedia
[*]**gimp** - Image editing
[*]**gimp-help-en** - english help file for GIMP, can be skipped
[*]**gimp-data-extras** - install with gimp above
[*]**firefox**(for Kubuntu only as it does not have firefox)
[*]**audacious** - a winamp look-alike
[*]**k3b** - burn baby burn, CD/DVD burning
[*]**libk3b6-extracodecs** - extra codecs for K3b
[*]**normalize-audio** - needed for K3b
[*]**sox** - needed for K3b
[*]**vcdimager** - needed for K3b
[*]**devede** - DVD authoring
[*]**audacity** - sound file editor
[*]**avidemux** - A demuxer, similar to VirtualDub
[*]**ffmpeg** - CLI video encoder
[*]**ffmpegthumbnailer** - make thumbnails of your movies like in Media Player Classic of Klite
[*]**transcode** - CLI video encoder
[*]**vlc** - multimedia player
[*]**libdvdcss2** - dvd decryptor
[*]**wine** - a Windows emulator
[*]**ttf-liberation**
[*]**libavformat-extra-52**
[*]**libpostproc-extra-51**
[*]**libswscale-extra-0**
[*]**ubuntu-restricted-extras** (Ubuntu only)
[*]**kubuntu-restricted-extras** (Kubuntu only)
[*]**xubuntu-restricted-extras** (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade.

Download the iso from here (Fast FTP link)
[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.10-64bit-aptoncd-20110204-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.10-64bit-aptoncd-20110204-CD1.iso)

Burn the iso to a cd.
 
Deployment: See [http://ubuntuforums.org/showthread.php?t=858425#5](http://ubuntuforums.org/showthread.php?t=858425#5)

---

### Post by nucleuskore on 2011-06-12
Hi
Here is the a list of applications for 11.04 only

Application list (June 2011)
[list]
[*]**htop** - an extension of top for viewing system processes
[*]**kchmviewer** - a CHM viewer
[*]**mplayer** - a multimedia player
[*]**gecko-mediaplayer** - a plugin for firefox to handle multimedia
[*]**timidity** - midi player
[*]**mozplugger** - optional but recommended plugin for firefox to handle multimedia
[*]**gimp** - Image editing
[*]**gimp-help-en** - english help file for GIMP, can be skipped
[*]**gimp-data-extras** - install with gimp above
[*]**firefox**(for Kubuntu only as it does not have firefox)
[*]**audacious** - a winamp look-alike
[*]**k3b** - burn baby burn, CD/DVD burning
[*]**libk3b6-extracodecs** - extra codecs for K3b
[*]**normalize-audio** - needed for K3b
[*]**sox** - needed for K3b
[*]**vcdimager** - needed for K3b
[*]**devede** - DVD authoring
[*]**audacity** - sound file editor
[*]**avidemux** - A demuxer, similar to VirtualDub
[*]**ffmpeg** - CLI video encoder
[*]**ffmpegthumbnailer** - make thumbnails of your movies like in Media Player Classic of Klite
[*]**transcode** - CLI video encoder
[*]**vlc** - multimedia player
[*]**libdvdcss2** - dvd decryptor
[*]**wine** - a Windows emulator
[*]**ttf-liberation**
[*]**libavformat-extra-52**
[*]**libpostproc-extra-51**
[*]**libswscale-extra-0**
[*]**ubuntu-restricted-extras** (Ubuntu only)
[*]**kubuntu-restricted-extras** (Kubuntu only)
[*]**xubuntu-restricted-extras** (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade.

Download the iso from here (Fast FTP link)
[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.10-64bit-aptoncd-20110204-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-11.04-32bit-aptoncd-20110612-CD1.iso)

Burn the iso to a cd.
 
Deployment: See [http://ubuntuforums.org/showthread.php?t=858425#5](http://ubuntuforums.org/showthread.php?t=858425#5)

---

