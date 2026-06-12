---
title: "Notebook: Cannot copy CD"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-05-24
I have installed 8.04.

I put in an Audio CD and right click on the icon and select copy CD.
A window pops up telling me that an image will be created. HOWEVER, that remains forever so without any progress.

I burned the Ubuntu iso to CD without any problem.

Any ideas what could be wrong? The log file says nothing about it.


bye

R.

---

### Post by Pumalite on 2008-05-24
What are you using to copy it?

---

### Post by ELMIT on 2008-05-24
What should I use? How do I know what is/not installed?

Ubuntu 8.04 clean installation.

bye

R.

---

### Post by Pumalite on 2008-05-24
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by ELMIT on 2008-05-24
We tried another CD, this time a movie and it worked. It seems only the Audio CD cannot be copied, ... without any error.

Thanks for the non-working link. 

bye

R.

---

### Post by Pumalite on 2008-05-24
In this article i describe some of the things to do immediately after installing ubuntu on your machine . Since most of the people reading this would be shifting
from Windows to Linux with a system dual booting so i would focus more on making transition easy from Windows to Linux.

Creating Your ultimate Ubuntu 7.10 Desktop

Ubuntu 7.10 Codenamed Gusty Gibbon was released few weeks back with much fanfare ,now Ubuntu for past couple of years has been one of the most popular Desktop Linux distributions . Ubuntu 7.10 includes a number of features , applets and Wizards to simplify desktop Linux experience however because of many licensing restrictions it does not include out of the box support for popular audio/video codecs and many commercial but good applications . Also because of the limitation of trying to accommodate all kind of applications on single CD Ubuntu comes with a limited set of applications .

Now , i often have arguments with my friends who are new to computers that windows is better , mac is better and blah blah blah and they often use this argument that it's difficult for newbies to install applications , codecs etc on Linux as a way to justify their arguments . So well i decided being such a Linux fanatic i have to do something about it so well i thought of writing a guide sort of step by step tutorial that would allow anyone to have a kicking Linux desktop with most of the codecs enabled and descent set of applications in few steps .

Steps Written in RED are of paramount importance and other steps may not work correctly if these steps are not followed .

Step 1 : - Enabling Additional Repositories

Now many applications need additional repositories to be installed or some to be enabled in Synaptic package manager so before trying out steps given below ensure that repositories in order.

Launch Synaptic Package Manager (System -> Administration -> Synaptic Package Manager ) , then in Synaptic package manager go to (Settings -> Repositories ) you will find window like this . Ensure that all the check boxes are marked leaving source code(if you want to you can enable this also but you are not going to need this unless you are software developer) the dialog box should look like this .
Dialog Box showing the repositories that should be enabled

After completing above step you will find a dialog box like this


Besides these you may also like to add medibuntu repositories if you want to install applications like ------- , to add mediubuntu repositories follow the following steps

    echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free" | sudo tee -a /etc/apt/sources.list


and

    wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update




2. Enabling Cool Graphics Effects

Unlike previous releases of Ubuntu where one had to manually download and install compiz,beryl etc (Compiz Fusion is composite window manager that provides best features of Compiz and Beryl) from Repositories if one wanted to have glitzy visual effects . Ubuntu 7.10 comes with Compiz Fusion pre-installed and on supported hardware offers a wide array of Visual Effect . Now depending on graphic hardware of computer one could chose from three level of Visual Effect (From System -> Preferences -> Appearance )

None : - This mode causes Ubuntu to use Metacity instead of Compiz Fusion , with no visual effect

Basic : - Has only simple visual effects like shadows , fading windows-menus etc

Advanced : - Recommended for PC with descent graphic hardware , enables effects like wobbly windows, transparency , animated workspace switching etc
Visual Effect Dialog Box
Now , the biggest advantage of Compiz Fusion is even on really slow hardware one can have descent set of visual effects even on my slow laptop i could use Extra graphics effects though it was painful while using application like OpenOffice because of my slow hardware.

However , compiz-fusion is capable of much more and you can enable more desktop effects /customize compiz by typing the following command in the terminal window : -

    sudo apt-get install compizconfig-settings-manager

After completing above step , you can customize compiz by going to System > Preferences > Advanced Desktop Effects Settings .

3. Installing Audio/Video Codecs

The first thing anyone who wants to use Ubuntu as a replacement to their windows operating system would like to do is install support for all kind of audio/video multimedia codecs . Ubuntu does not come installed with support for major audio/video formats because of licensing issue and other issues . To install support for audio/video codecs type in the following command in the terminal window : -

    sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly

And if you want to install mp3 support in nautilus you may like to install mpg123 which is a nice command line based utility for playing mp3 files and it works well even on modest hardware .

    sudo apt-get install mpg123


This would enable most of the popularly used codecs in the Totem Movie player which uses the GStreamer framework to play audio/video files.

If you want to use a different media player and framework you might try installing MPlayer or VLC (depending on which you prefer ) instructions on installing them are listed below .

Installing VLC Player : -

LC Player is another of popular video player available under Linux . It is released under GNU General Public license and is available for different platform including Windows,Linux,BeOS,Mac OS X etc. VLC player is based upon free open source libraries like libdvdcss,FFMpeg for decoding various video formats.One Important feature of VLC Player is it's ability to play files over NetWork Protocols. The Frontend of VLC player is created using wxWidgets toolkit and it's appearance can be changed by using different skins. One Popular feature of VLC Player is it's ability to play files that are incomplete/broken or partially downloaded , making it useful for previewing file while downloading on file-sharing networks.

To install VLC Player type the following command in the terminal window : -

    sudo apt-get install vlc


After completing above step launch vlc player from (Applications -> Sound and Video -> VLC media player )


3. Installing Linux DC++ Client

DC++ is a popuar tool used for p2p file sharing and is especially popular in college campuses , to install dc++ for linux follow the following instructions .

Type the following command in the terminal window: -

    sudo apt-get install linuxdcpp

And after completing above step launch dcpp from (Applications -> Internet -> DC++)
Linux Client of popular DC++ Application


aMule

aMule is alternative to popular eMule program on windows platform , amule supports/works with eDonkey2000 Network or Kadnetwork and allows P2P sharing of files . aMule is available on number of platforms , Current supported systems include Linux, Mac OS X, FreeBSD, NetBSD, OpenBSD, Windows and Solaris.

To install aMule type the following command in the terminal window : -

    sudo aptitude install amule

After completing above step launch aMule from (Application -> Internet -> aMule )


4. Installing Adobe Acrobat Reader

* Requires Mediubuntu repositories

Type in the following command in the terminal window :

    sudo aptitude install acroread acroread-plugins acroread-escript



and , plugin for firefox

    sudo aptitude install mozilla-acroread



5. Installing Macromedia Flash support and Sun Java JRE

Both Macromedia Flash and JRE are an important part of internet experience almost all the websites use either of the two technology to add extra functionality to the web page . By default Ubuntu does not come preinstalled with support for these two , however they can be installed quite easily by typing in the following command in the terminal window .

To install flash type in the following command in the terminal window this command is going to download a script that would further download the files needed for installing flash-support and install it .

    sudo apt-get install flashplugin-nonfree

Script downloading further files needed for installing flash support



and to install Sun Java JRE type in the following command in the terminal window .

    sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts


6. Scribus

Scribus is one of the most impressive Desktop Publishing application that is free and cross platform . Scribus is available on Windows , Mac OS X , Linux , OS/2 etc . It is highly suited for preparing file for professional quality image setting equipment .It has high end page layout features of the kind found in Adobe PageMaker, QuarkXPress and Adobe InDesign.

It can also create animated and interactive PDF presentations and forms. Example uses include writing small newspapers, brochures, newsletters, posters and books.

Anyways , to install scribus type the following command in the terminal (Application ->Accessories -> Terminal )

    sudo aptitude install scribus

and after completing above step launch scribus by typing "scribus" in terminal window.
Scribus on Ubuntu

7. Downloader For X

Downloader for X is a nice download manager that allows downloading files from Internet , pausing them and downloading them later . It also supports splitting file into number of segments so that files could be downloaded quickly . However one thing that i didn't like about is it's interface is somewhat difficult as compared to some of the download manager available on Windows.

Anyways to install " Downloader for X " type the following command in the terminal window.

    ¨sudo aptitude install d4x "



After installation is over launch ¨Downloader for X¨ by typing ¨d4x¨ in the terminal window , or by going to (Applications-> Internet -> Downloader for X )


This is how Downloader for X looks




8. Google Desktop

Google Desktop allows one to full text search of a user's e-mail, computer files, music, photos, chat, and Web pages viewed,OpenOffice documents , PDF files and more .

Now similar tools already existed on Linux like beagle (supported by novell ) , meta tracker etc . However Google Desktop search is not based on any of these tools and uses its proprietary algorithms to search for files on the computer ,also being 1.0 release and more stable then these products it could be preferred over tools like beagle .


To install type the following command in the terminal window : -


    wget [http://dl.google.com/linux/google-repo-setup.sh](http://dl.google.com/linux/google-repo-setup.sh)



and

    sudo bash google-repo-setup.sh



Now after completing above steps to install Google Desktop Search type the following command in the terminal window : -

    sudo apt-get update


and

    sudo apt-get install google-desktop-linux


After completing above step logout of gnome session and relogin you would find the following dialog window

select the appropriate option : -


Now after choosing appropriate option you would find Google Desktop icon in the bar at the top of the screen , now it would automatically scan and index files on computer and store it in local database which could be searched using web browser .


9. Google Picasa

Google Picasa is an extremely professional good looking photo management application available on Windows ,Linux and Mac OS (??) . Now Google Picasa has a number of features that many photo management software on Linux dont have further Google Picasa looks very user friendly as compared to similar open source application available on linux . Now Google Picasa for Linux is not a native linux application but runs on Linux thru application layer called wine which allows many windows application to run flawlessly on Linux.

Now to install Google - Picasa type the following command in the terminal window

    wget [http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.2.2820-5_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.2.2820-5_i386.deb)

and

    sudo dpkg -i picasa_2.2.2820-5_i386.deb

After completing above step launch Google Picasa from


Some Tips to consider before running picasa (taken from google picasa website )

Tips

    * If you use NFS, when Picasa first starts, tell it to scan just your desktop! Otherwise Picasa gets real slow while it scans all your NFS directories!
    * To get Picasa to see pictures on your hard drive, click "File / Add Folder" (NOT "Import").
    * When adding a folder to Picasa, the default action is to remove the folder from Picasa. You have to actively choose Scan once or Scan always.
    * Picasa is not supported over remote X connections. 

10. Google Earth

To install Google Earth type the following command in the Terminal Window (Application->Accessories -> Terminal ),keep in mind that googleearth is downloaded from Medibuntu repositories and not Ubuntu hence be sure you have activated the repositories correctly as described in first step of this article.

¨sudo aptitude install googleearth"

After downloading is over you will get a screen like this press ¨Yes¨ to accept the license agreement and complete software installation.


Now you can launch Google Earth from (Application -> Internet -> Google Earth)

A Picture of Google Earth Running on linux


11. Installing gdesklets

gdesklets gives user a collection of impressive widgets that can be placed on desktop this is similar to feature available on Windows Vista and Mac OS X , it does provide quite a good look to the desktop.

To install gdesklets issue the following command at the command line


sudo apt-get install -y gdesklets

after installation go to (System -> Preferences -> Sessions) There go to Start up program and add gdesklets shell , now every time gnome loads up you should see your gdesklets on the desktop.

This is how my desktop looked like with all the desklets (Widgets )

12. Installing MPlayer with all codecs and dvd playing support

*This step requires Medibuntu repositories

MPlayer is one of the most popular media player available on linux , it supports playing all the major audio/video file formats . With w32codecs and libdvdcss2 it plays all the major audio/video format,however w32codecs has dll files from windows operating system hence its not available on the ubuntu official repositories and needs to be downloaded from the mediubuntu repositories.

To install MPlayer with all codecs type in the following command in the terminal window : -

    sudo apt-get install mplayer



and

    sudo apt-get install w32codecs libdvdcss2




After completing above steps you could launch MPlayer by typing in gmplayer in the terminal window or from (Application -> Sound & Video -> MPlayer Movie Player )


Quod Libet : -

Quod Libet is an extremely versatile music player based on GTK+ that is extendible via plugins , has a rich feature set and has really unique feature of building playlist by searching for particular kind of music files based on search terms or regular expression . It has been programmed in Python programming language and hence it's plugin are also created in Python. A number of plugins are available including ones that help in copying songs to digital audio players , last.fm plugin , advanced editing features and many more .

Quod Libet uses GStreamer framework of GNOME to play audio files and hence integrates quite well the the GNOME desktop environment , also audio format supported would be same as the one supported by GStreamer so you may want to install mp3 support since by default many linux distributions these days dont come with mp3 support installed.

To install Quod Libet type the following command in the Terminal Window : -

    sudo apt-get install quodlibet

and after completing above step launch quod-libet from (Application -> Sound & Video -> Quod Libet )

Quod Libet Website : - [http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet)


13. RealPlayer

Realplayer is one of the most popular cross platform media player available on Windows,Linux , Mac OS and a number of other platform . RealPlayer plays popular .rm ,rmvb,.mp3 and other media formats.

To install RealPlayer first download RealPlayer10GOLD.bin file from the following website assuming you have downloaded it to your home directory .

After downloading the file go to the directory where you have downloaded the file in terminal window and type

After installation is over type

¨chmod +x RealPlayer10GOLD.bin¨

and

¨sudo ./RealPlayer10GOLD.bin¨

for installation to begin . Follow the instructions as presented to complete installation .

After installation is over you can launch Real Player from (Application -> Sound & Video -> Real Player 10 ).

Real Player for Linux




Article Written by : Ambuj Varshney (blogambuj@gmail.com)
For Linux on Desktop , [http://linuxondesktop.blogspot.com](http://linuxondesktop.blogspot.com)
(C) 2007 , Ambuj Varshney


PART BELOW IS AN OLDER ARTICLE (Orignal one i had written sometimes back for Ubuntu 6.10)

1. Enabling/Adding Extra Repositories
Ubuntu comes by default with only some of the repositories enabled because of licensing issue since downloading certain codecs and apps may be illegal in some countries so you have to enable these repositories/add new repositories to enable installation of these packages.

To enable new repositories go to (System -> Administration -> Synaptic Package Manager ) , type in the root password .Then Go to (Settings -> Repositories ), there enable all the check-boxes to enable all the repositories you need .


Also for installing some apps extra repositories are needed since they are not in the default repositories so go to third Party and add the following there


deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all

This repositories below is for Multimedia files and stuff above was for ntfs-3g you can use any one of the above since they are mirrors.

deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all


IMPORTANT: Do not press reload button now in synaptic package manager type first following command in the terminal to install the GPG keys.

After doing this exit Synaptic Package Manager go to (Applications > Accessories > Terminal) and type the following command to import GPG keys .

wget [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc) -O- | sudo apt-key add -

wget [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg) -O- | sudo apt-key add -


After doing this your system should be ready for installing extra application. Type the

sudo apt-get update
sudo apt-get upgrade

at terminal to start adding data from the repositories.

2. Installing ntfs-3g

ntfs-3g this is necessary if you have a ntfs drive in your computer ( Usually Windows XP installs on NTFS drive) and you want to read and write data to the drive you have to install this .

This can be installed as following type the following at the command prompt

sudo apt-get update
sudo apt-get upgrade


sudo apt-get install ntfs-config


Then type the following command

gksu ntfs-config


This is automatic configuration of ntfs-3g , enable read , write support and it should be configured.


these commands would back up fstab file if configuration goes wrong.

sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab

Now one more thing you want your windows (NTFS) drive to be mounted automatically add the following entries to /etc/fstab
/dev/ /media/ ntfs-3g defaults,locale=en_US.utf8 0 0

Where /dev/partition is the partition which is NTFS drive , in my case /dev/hda1
/media/ this is just the directory you want to use as a mount point where windows drive would be mounted , you can very well use any drive you like.

now Restart ubuntu your windows partition should be working well.

3. Making Windows see your Linux partition


Windows XP lacks support for reading and writing files to Linux file system however external utilities like free Ext2 File system for windows allows Windows XP to read and write files to a Ext2 , Ext3 file system however ReiserFS file system is not supported .

You can get Ext2 file system for windows at the following link : -
([www.fs-driver.org/download.htm](www.fs-driver.org/download.htm))


4. Installing flash-plugin

Macromedia Flash player is not installed by default but since we would be surely needing it while browing the net , installing it is necessary
it can be installed by following command


sudo apt-get install -y flashplugin-nonfree


5. Installing Microsoft True Type Fonts

If you are making a jump from windows to ubuntu you would surely miss the true type fonts that Windows uses , since Microsoft has released them free so they can be installed without a hitch in ubuntu (Though not distributed with Ubuntu) .


sudo apt-get install -y msttcorefonts


6. Installing unrar

RAR is one of the very widely used archives on Windows , however unrar tool to decompress RAR is not shipped with distribution and has ti be installed manually.


sudo apt-get -y install unrar 



7. Installing mpg123

mpg123 is a very nice command line based mp3 player that can play mp3 files even on a slow processor based computer , further installing this provides a way of playing mp3 files from within the nautilus file manager . Hence i recommend installing mpg123


sudo apt-get install -y mpg123


8. Installing Adobe Reader

Though ubuntu comes with default evince reader for viewing pdf files , but i am sure you would like to use more complete version of pdf reader Adobe Reader 7.0 which is quiet professional and
more robust , the Linux version of Adobe Reader 8.0 has not been released but the version 7.0 is available and could be downloaded from the following website : -

[http://www.adobe.com/support/downloads/product.jsp?product=10&platform=unix](http://www.adobe.com/support/downloads/product.jsp?product=10&platform=unix)


9. Installing DVD playback support

Now this is a contentious issue , in some countries playing DVD files through DEcss is illegal so use it at your own will , anyways to enable dvd playback issue the following command at the command line : -


sudo aptitude install libdvdcss2



Note : the above commands would only work if you have added the repositories i had mentioned before the Seveas repositories.

However if you do not have these Repositories installed issue the following command to install the DVD playback support : -


sudo /usr/share/doc/libdvdread3/./install-css.sh



10 . Installing the extra multimedia codecs,players

Now you would surely want to install all the codecs for playing various media files and the players primarily xine,vlc,mplayer issue the following commands to install the multimedia codecs.


sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
vlc mplayer


This command would install most of the codecs for gstreamer multimedia architecture and vlc media player and Mplayer , as well as the dll files codec (w32codecs) for decoding various files whoose open source decoder are not available.

11. Updating the system
After installing Ubuntu you would surely like to update the system so that all the packages on the system are up to date to new version of the software .
It can be done by following steps , go to (System > Administration > Update Manager)
Now press the Check button and then Install updates to start the installation of updates to the ubuntu system.


12 . Installing beagle

Now Ubuntu does not come with beagle pre-installed maybe because it is still not a final 1.0 release still it is very nice and efficient for searching files and directories on Linux providing features similar to Google Desktop Search and Mac OS Spotlight anyways to install beagle issue the following command at command line :


sudo apt-get install -y beagle




13. Installing gdesklets

gdesklets gives user a collection of impressive widgets that can be placed on desktop this is similar to feature available on Windows Vista and Mac OS X , it does provide quite a good look to the desktop.

To install gdesklets issue the following command at the command line


sudo apt-get install -y gdesklets

after installation go to (System -> Preferences -> Sessions) There go to Start up program and add gdesklets shell , now every time gnome loads up you should see your gdesklets on the desktop.

This is how my desktop looked like with all the desklets (Widgets )


Late additions:-
If you find above steps complicated and would like to do it simple way try EasyUbuntu described below , since Automatix have not been well received by Ubuntu Developers and is somehwhat similar in features to EasyUbuntu i am describing EasyUbuntu only.

EasyUbuntu is a community maintained script that provides a easy way of installing most of the codecs , applications ,tweaks not included in official ubuntu installation. Initially there were fears that attracted a lot of negative publicity to the EasyUbuntu script that is it forces application installations and modifies systems sources.list however according to official EasyUbuntu website these problems have been corrected .

Some of the packages it installs include following : -
(Note : taken from official EasyUbuntu Website )

Multimedia

    * Enhance video player: Install a better multimedia backend (totem-xine replace totem-gstreamer)
    * Free Codecs: Add Support for playing mp3 and other non-free formats
    * Binary Codecs: Add support for proprietary video and audio formats (w32codecs) (only x86)
    * libdvdcss: Read commercial and encrypted DVDs
    * MIDI: Add support for playing midi files

Web

    * Flash: Enable the Macromedia Flash plugin (only x86)
    * Java: Enable the Java plugin (Sun Java for x86, amd64) (IBM java for ppc)
    * Videos: Enable viewing videos embedded in webpages

Archives

    * RAR: extract and create RAR archives
    * ACE: extract ACE archives
    * 7-Zip: Extract 7-Zip archives

System

    * Repository list: Main, Universe, Multiverse and PLF (replace your previous sources.list)
    * Fonts: Install Microsoft and other nice fonts
    * DMA: Enable Direct Memory Access to improve DVD reading (breezy)
    * Nvidia: install the official driver to enable 3D on Nvidia graphics cards
    * ATI: install the official driver to enable 3D on ATI graphics cards

Voice Over IP

    * Wengo: a free Voice Over IP software (available in dapper)
    * Skype: the most popular VoIP software (only x86) 


Installation : -

To install EasyUbuntu first download the Ubuntu package from the following link:

[http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb](http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb)

now go to (Application -> Accessories -> Terminal) and go to the directory where you have downloaded the debian package of EasyUbuntu and issue the following command to install EasyUbuntu : -

sudo dpkg -i easyubuntu_latest.deb

after completeion of the above process issue the following command in terminal

sudo wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -


Now EasyUbuntu should be set up for installation of packages .


Go to (Applications -> System tools -> EasyUbuntu ) to launch EasyUbuntu , beyond this the applications interface is quite easy for beginner and one can easily install packages without much help.



Automatix is another community maintained script , similar to EasyUbuntu simplifies the installation of the commonly used codec(Mp3,Video formats, Flash 9 and more ),applications(like Google Earth,Picassa,VMWare Player and more) there has been both positive and negative things said about Automatix , personally i have not used it but i have heard a lot more positives than negatives in using Automatix ,However German version (not officially supported by the Automatix team) has some serious issues currently: removes its own files instead of using the packaging system. uses apt-get --force and --assume-yes anyways some of the programs and is not officially supported by Automatix team.

However Automatix has received some serious comments from Ubuntu Community which have criticized it since it makes Upgrading Ubuntu difficult since it adds it own repos.

Ubuntu CTO Matt Zimmerman said "I cannot recommend the use of this program, and systems where it has been used cannot be supported with a clean and official upgrade path. , and Some individual Ubuntu developers blamed Automatix 1 for breaking updates from Dapper to Edgy

So i am not describing it here .



Article written by : -
Ambuj Varshney
For Linux On Desktop ([http://linuxondesktop.blogspot.com](http://linuxondesktop.blogspot.com))
(C) 2007 Linux on Desktop

IMPORTANT : I will not be responsible for any loss of data suffered by you by using the commands in this article i have tried to make the document as correct according to my knowledge further i have tried removing certain things and improved certain points based on comments of users . If you have anything to say/improve/correct in article please comment .

Also about repositories , well what i have added was from reputed sources first 3 were of ntfs-3g now of which one was not working i have removed the link now for remaining links well you can go to official website of ntfs-3g([http://www.ntfs-3g.org](http://www.ntfs-3g.org)) There if you click on Ubuntu it takes you to a page of Ubuntu Forums describing method for installing ntfs-3g([http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)) since the forum topic has been well received and has been referred by the offical ntfs-3g site so i linked it.

Also about the last repositories link it is of official ubuntu Netherlands site so should not be a problem.

About automatix2 and easybuntu well they can simplify the job mentioned here but i decided to follow a different approach and i have mentioned here , you are welcome to try them out and maybe i would review them also later.

Thank You

Labels: Tutorials, Ubuntu, Ubuntu Customization
Stumble Upon ToolbarStumble It! del.icio.us   &#9830;Add to Technorati Faves


# posted by Ambuj : 2:18 PM
Google
Enter your search terms
Web 	linuxondesktop.blogspot.com
Submit search form
Comments:
It's really a pain doing that everytime you install ubuntu. There's a little app that automatically downloads and installs most of the stuff you talk about here, its called easyubuntu ([http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/))
# posted by Blogger Quique : 9:37 AM
 
Or you could just install Automatix.
# posted by Anonymous Justin : 9:38 AM
 
That link in step 3 should be [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Also, the package name in step 2 is ntfs-3g, not ntfs-config.

And the automatic tools listed above really do take all the (unnecessary) complexity out of it.
# posted by Anonymous Anonymous : 9:56 AM
 
Yes you could use automatix or easybuntu but they add their own repos and some stuff dont work well !!! and moreever when things can work perfectly well by typing (Copying pasting ) few line of text why would you like to use automatic tools that give you half control over what u are doing . And isnt doing by this method more learning for the newbies as they learn abt apt-get,etc fstab and more they are more closer to actual process .
# posted by Blogger AMBUJ : 9:59 AM
 
Yes the link was wrong, but the thing abt ntfs-config you mentioned ntfs-config is for automatic installation it installs ntfs-3g itself so no need to install it separately
Cheers !!.
# posted by Blogger AMBUJ : 10:04 AM
 
one question? where can i find the icon themes you are using?


Thanks
# posted by Anonymous Anonymous : 10:14 AM
 
What gives you the OSX like dock at the bottom?
# posted by Anonymous Anonymous : 10:18 AM
 
To quote ubotu the Ubuntu irc channel help bot: "automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to install a fresh copy of Ubuntu."

Tread carefully if you choose this route.
# posted by Anonymous Anonymous : 10:37 AM
 
I forgot to say in my post above about automatix, that they give a similar warning for easyubuntu, but are a little nicer about it:
"easyubuntu is a script that automates installation of some items. Use at your own risk. See [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) "
# posted by Anonymous Anonymous : 10:41 AM
 
In FreeBSD ports they have a thing called a "meta-port" which just installs a list of other ports. There's one like this called "instant-workstation" (at /usr/ports/misc/instant-workstation). Can save a lot of time, just type "make install" once.
# posted by Anonymous kace : 10:47 AM
 
Never had a problem with Automatix
# posted by Anonymous Anonymous : 11:03 AM
 
I use kubuntu and both easyubuntu and automatix have both given me trouble this method would probably work more gracefully thanks for the tips
# posted by Anonymous Anonymous : 11:28 AM
 
Or you could just wait until April when Feisty comes out, and 3/4 of your steps are deprecated since all those "restricted" modules and packages are installed by default...
# posted by Anonymous Anonymous : 11:32 AM
 
Nice article for the community new to Linux. These are certainly all good things one should do to prevent from being 'homesick' of windows functionality.

I'd like to be the first to say Great Job, aside from someone to just point out something thats WRONG.
# posted by Anonymous Anonymous : 11:42 AM
 
Adobe Reader can also be installed from the repositories...

sudo apt-get install -y acroread
# posted by Anonymous Anonymous : 11:52 AM
 
Don't forget flpsed, the best PDF editor ever.
# posted by Blogger Erik : 1:39 PM
 
evince is easily enough for your average pdf viewer/user. Adobe is just slower at doing the same thing, although I haven't tried flpsed. I would recommend Automatix for the new users as it's very simple to use.

I would also say that gdesklets are a useless addition - calendar and clock are already intergrated into the panel (with Evolution support)
# posted by Blogger Jack : 3:55 PM
 
the OS X like dock at the bottom comes with the gdesklets
# posted by Anonymous Anonymous : 4:25 PM
 
Steps 7, 9 and 10 can be substituted by installing the excellent MPlayer.

note for 64bit users: You won't be able to use the win32 codecs, so the ubuntu package version won't play wmv, for instance. I had to compile my own version, and now it plays everything, natively. But don't be afraid, it's way easier to compile MPlayer than some steps described here. :)
# posted by Anonymous Anonymous : 4:29 PM
 
I really love to find such blogs of ppl sharing their experiences , and make other ppl's life easier
BTW , many of us meet frequently at
irc:/irc.freenode.net/ubuntu
irc:/irc.freenode.net/kubuntu and siblings
keep sharing
cheers
# posted by Blogger tonybehar : 4:56 PM
 
It might be simpler to use linuxmint.

At least until Feisty is available....
# posted by Blogger tregeagle : 5:08 PM
 
Cool, thanks a lot for those hints! I'm new to Linux, so they're very helpful.
# posted by Anonymous Anonymous : 6:08 PM
 
I have automatix and it works great !!!
# posted by Blogger Asim : 6:58 PM
 
You may want to try kpdf instead of adobe acrobat reader. It's an open source solution and actually works quite well even if you are using the gnome desktop (which you likely are if you are running Ubuntu).
# posted by Anonymous Anonymous : 7:46 PM
 
does anyone know if the windows partition trick will erase all the data on the drive? i have a drive that windows formatted thats a backup drive that i want ubuntu to recognize, would this kill it? thanks
# posted by Anonymous Anonymous : 8:55 PM
 
The very firt thing I do is enable SSH for remote login
# posted by Blogger PacoVMS : 9:22 PM
 
The official Ubuntu support channel would like to kill anyone who uses Automatix. :)
# posted by Blogger Ender : 9:44 PM
 
You should make some modification on step 2 :
1. The three repo
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) edgy main main-all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
are three different mirror of the same repo, so just one is enough
2. You do 2 times the same things : ntfs-config configure automatically your fstab, so there is no need to change it after that.
# posted by Blogger Florent : 9:52 PM
 
It's telling now that several of the most important of these things (dvd playback, ntfs access, mp3 playback) are workarounds for stuff that linux can do _technically_ but not _legally_, at least in the USA. All this stuff could be out-of-box functionality for linux desktops, were it not for the laws of the Corporate Reich of America.


Linux is technically ready for The Desktop (tm), has been for ages. The USA's corporatist legal system is simply blocking it to protect Microsoft.

Remember folks, what's good for General Motors^W^W Microsoft is good for America....

Yeah, right...
# posted by Anonymous Anonymous : 9:54 PM
 
This post has been removed by a blog administrator.
# posted by Anonymous Anonymous : 10:55 PM
 
This is a pretty good list, but it also sadly sums up the reason that Linux is a far, far distant third to OSX and Windows in terms of mass market appeal. Command line installs? Sure, they're ok with all of us who are reading this page (or Digg), but if you're reading this page, you're already a geek. Most people would read this page and run out to buy Vista out of sheer fear of complexity.
# posted by Blogger sohonyc : 11:01 PM
 
Something is wrong in step two.
I think one or two of the links indicated for Edgy ran out of bandwitch, therefore no way of downloading it. Could some say where to find it?
# posted by Anonymous Anonymous : 11:46 PM
 
"sudo aptitude install libdvdcss2"

Yup, Linux is ready for the desktop any day now
# posted by Anonymous Anonymous : 11:57 PM
 
Any day now. Linux will be ready for the desktop any day.

Among typical users: ESP practionners, Oracles and divinators.
# posted by Anonymous Anonymous : 11:59 PM
 
Ambuj, you criticize Automatix and Easybuntu because "they add their own repos", but then your very own step 1 recommends that people add the repositories you specify. So is adding unknown third-party repositories a good idea, or not?

Here's a hint: It's a very bad idea. It's irresponsible of you to recommend to anyone who finds your page that they add those repositories, without even mentioning who provides each of them and what they contain. For example, the first repository you give doesn't even exist, but the domain is that of a free Web hosting company. What if someone signs up for the givre.cabspace.com account and starts using it to provide packages that claim to be new versions of things in Ubuntu, but are actually viruses and spyware?
# posted by Anonymous Anonymous : 12:04 AM
 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://givre.cabspace.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://givre.cabspace.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 302 Found
[http://givre.cabspace.com/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz:](http://givre.cabspace.com/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz:) 302 Found
# posted by Anonymous Anonymous : 12:07 AM
 
Or you could just forget the whole crap and just use Windows or OSX.
# posted by Anonymous Anonymous : 1:51 AM
 
You don't need to use the command line to install most of these things. Just search for the same name "ntfs-3g", etc. in the Synaptic Package Manager.
# posted by Blogger M : 2:40 AM
 
Better yet save yourself all the headaches involved with *buntu and install Debian.
# posted by Blogger craigevil : 4:09 AM
 
How do I get better wireless support. So far it seems I have to know the SSID of the wireless network and I'm limited to WEP. Is there a simple wireless manager I can install that will show me what networks are available (Including WPA, etc..)
# posted by Anonymous Anonymous : 4:18 AM
 
No Beryl?
# posted by Anonymous Anonymous : 6:28 AM
 
Linux is not ready for desktop, because it excludes two types of users:

Gamers. Sorry folks, you can try to reason all you want but gaming does not work on Linux at the moment.

Graphic Designers. Gimp doesn't cut the mustard and emulated Photoshop makes me sick.

These are LARGE communities.

Makes me sad. I keep forcing myself to use Linux all the time, but then I always hit those two walls. Bah.
# posted by Anonymous Anonymous : 8:49 AM
 
there is also the easy way, in just one step:
1) install Linux Mint.
save about 2 hours of your time and spend it seeing friends and having a drink
# posted by Blogger Hannes Pasqualini : 7:51 PM
 
Er, is this the MS Vista forum? I run windoze and I don't really know what I'm doing.
# posted by Blogger Shag : 10:01 PM
 
You say "fire up console" but there is no "console" in the standard menus. Presume you mean Applications > Accessories > Terminal? But if so, and if truly speaking to "newbies" you had better be explicit & exact.

When you close the add-repository dialog in Synaptic it tells you "you have to click on the Reload button..." but if you (the newbie, remember?) do that, you get an obscure (to a newbie) error message about no "no public key." Presumably the following "wget" steps are supposed to fix that? You might warn the user not to click reload.

In fact altho I ran the wget steps and killed and restarted Synaptic, it still got a no-key error message. So I deleted the added repositories and gave up (like a newbie would).
# posted by Blogger dcortesi : 11:30 PM
 
"sudo aptitude install libdvdcss2"

Yup, Linux is ready for the desktop any day now


the advantage of command lines like this is the user can just copy it from the web and paste it into the terminal. hit enter and it's installed. ever try to get DVDs plyaing on windows....for free?

#14 remove ubuntu and go back to slackware.....

i kid, i realize this guide's not for me, but honestly that's what i ended up doing. i gave ubuntu a try for a while, and even turned a few people onto it, but in the end, i love slack. certainly not the easiest distro, but it does what you want it too quickly, and not much more.
# posted by Blogger cmorgan47 : 12:10 AM
 
Gotta take issue with step #8...you're sure we'd like to use Adobe Reader? I've taken all Adobe software off my computer, and it was one of the best decisions I ever made =)

-Es
# posted by Anonymous Anonymous : 1:09 AM
 
sohonyc said... "Most people would read this page and run out to buy Vista out of sheer fear of complexity."

Give me a break! Windows administration is painful.

Do you enjoy be a clicker?

Anti-* software wastes a lot of YOUR resources.

The MS-way to handle computing complexity is only denial.

Invest your money better!
# posted by Anonymous Anonymous : 2:11 AM
 
Hello thanks for the comments
made change to the step on adding repositories to add GPG keys and then click reload button .
Thanx to the reader who pointed this out
# posted by Blogger AMBUJ : 2:43 AM
 
So does this all work on dual-core AMD boxen yet? Last time I tried, there were a few items not yet available on the AMD dual core platforms...
# posted by Blogger Chris : 5:29 AM
 
Surely instead of rebooting to re-read fstab, running
sudo mount-a would be quicker?

If automatix crashes (which it does a lot) in mid-install, then it's a ******* to fix. It also installs a couple of things in stupid places. I'd never recommend it, and I've installed a lot of ubuntu systems.

One final point - personally instead of using hacks to support extfs in windows and ntfs in linux, I'd create a shared fat32 data partition since the only things to bother sharing would be data like movies and music.
# posted by Anonymous Anonymous : 2:33 PM
 
One more vote for Linux Mint! It really is the easiest Linux distro at the moment. Works out of the box, really.
# posted by Anonymous kuvittelija : 1:58 AM
 
I'm pretty new to Linux (I've run OpenSuse, but didn't keep it long, but I'm willing to give Linux a shot again with Ubuntu). Anyway, I get stuck in step 1! :(

When I do this part:

wget [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc) -O- | sudo apt-key add -

wget [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg) -O- | sudo apt-key add -

I get something that looks like your screenshot, except I never get the "OK" and it doesn't let me type in the terminal again (as in the cursor is there and blinking, but typing does nothing)... How long should that step take? More than 10 minutes?
Thanks for this guide! :)
# posted by Anonymous Robby : 6:52 PM
 
Decent article; may I suggest a step 14?

14. Figure out why JPEG isn't a good format for screenshots, and you should use PNG instead.

:)
# posted by Blogger jsled : 12:11 AM
 
Hello Robby

well i tried those commands and they worked well on my laptop it took around 3 minutes , so maybe you can try to run them again also netwrok may be down there or someother reason.

cheers
# posted by Blogger AMBUJ : 2:16 AM
 
Uhm, you know the part where it says:

"IMPORTANT: Do not press reload button now in synaptic package manager type first following command in the terminal to install the GPG keys."

What do you do if you do press it? Is there a way to rollback?

Ps:. by the time I scrolled down to see the warning my dumb *** had already clicked the "Reload button"
# posted by Blogger B. : 10:12 AM
 
I figured out why I was never getting OK! :)

I never switched to root when I was in the terminal. I noticed that you were logged in as root in the screenshots. Once I switched to root, all went off like a charm! :)
# posted by Anonymous Robby : 4:07 AM
 
Installing ntfs-3g didn't work following these directions(it kept hanging on getting the GPG keys), but it did following the directions from this site Ubuntu Forum Thread
# posted by Anonymous Anonymous : 7:46 AM
 
You forgot to add:

14. Cry about the fact that you can't run Adobe apps unless you wine/virtual/hack your want into running the windows versions, and then reboot into Windows. (And don't forget adobe makes more apps than photoshop).
# posted by Anonymous Anonymous : 1:18 AM
 
I have just installed Ubuntu..server editionb..and now have reinstalled the desktopCD due to lack of command line knowledge. Now I am at least moving forward. I will go back through this post and do each step as written after looking at the 58 comments to see if they were written incorrectly. Is it possible there is a "clean" 13 steps with the mistakes fixed?anyone game for rewriting this post? If you do, please shoot off fireworks so I can have it a little easier. Hope I do well with this and will report back with documentation.
# posted by Blogger Lee : 4:41 PM
 
hello guys i am new at linux and i have a problem with my net card.the system can not find it.how can i restore it?plz if anybody knows how i would like to send me an e-mail in [email]fuzer1988@hotmail.com[/email]!also i am greek!thank you very much!
# posted by Anonymous Anonymous : 3:31 AM
 
Hi,

There are so many wrong things in this post I can't comment them all.

I'll only summarize by saying this:

- almost none of the mentioned packages needs to be installed from command line, just use synaptic. Many packages can be installed with one single command:
sudo apt-get install package1 package2 package3....
- it's OK to use third party repositories if you know the risks involved: not getting security updates, having to trust their developers, possibly getting unwanted updates to official packages, possible having a broken update path for Ubuntu's next version
- An update of all your system will be automatically offered shortly after install. You can do it manually, however, but I'd suggest doing it as soon as the install is finished.
- Finally, most of this information will be outdated by the time Ubuntu 7.04 (Feisty Fawn) comes out.

I particularly like the numerous warnings at the end of the post.
# posted by Anonymous Anonymous : 7:48 AM
 
Hello, Someone mentioned the wireless problem and I have found this as one of the most used software I installed. There is an application called wifi-radar avalible in the apt-get repositories that is essential especially if you hibernate your computer alot. You lose your connection and it is so much easier than using iwconfig. You may want to add a small step for laptop users.
# posted by Anonymous Anonymous : 5:03 AM
 
This post has been removed by a blog administrator.
# posted by Blogger suwit : 2:17 PM
 
de 13 pasos al menos 4 ó 5 dedicados a software propietario. ¿Puede dar más asco?. No.
# posted by Anonymous r0sk : 1:49 PM
 
so cool
# posted by Anonymous lounge : 12:08 AM
 
This post has been removed by the author.
# posted by Blogger Shahryar Ghazi : 1:46 AM
 
nice try!

I wrote something similar here
Installing and Hardening Debian
# posted by Blogger Shahryar Ghazi : 1:48 AM
 
I can think of a lot more important things to do than installing Adobe Reader or RAR. In fact, when I'm forced to open a .pdf file or extract files using RAR I tend to cringe.
# posted by Anonymous Anonymous : 9:39 PM
 
I read this article almost immediately after installing Ubuntu the first time. It told me I could use EasyUbuntu, and that thing caused me many more problems down the road. I suggest instead starting with a blank slate. You can read about my Ubuntu experience at Ubuntu For Free.
# posted by Blogger Good Time Tribe : 6:39 AM
 
Thanks for the nice post!
# posted by Anonymous free ps3 : 4:31 PM
 
Windows is still much easier to navigate. Ubuntu HAS made some great strides but still lacks the simplicity of Windows for use, upgrading and installing applications.
Another 5 years.
# posted by Anonymous Anonymous : 7:58 AM
 
Post a Comment

Subscribe to Post Comments [Atom]




<< Home

This page is powered by Blogger. Isn't yours?

Subscribe to Posts [Atom]

 Subscribe in a reader
What is RSS?

    * Using Archives on Linux
    * DreamLinux 2.2 : Review - A Nice Linux based OS ba...
    * Eleven Really usefull Linux Tips
    * Get Yourself Ubuntu Stickers
    * installing Ubuntu on old computers
    * A CASUAL GUIDE TO SOME COMMONLY USED LINUX COMMA...
    * Downloading and Converting YouTube Videos for Mobi...
    * Playing Audio/Video Files under Linux
    * Displaying Resolution Correctly on WideScreen Lapt...
    * Installing Applications Under Linux

Labels

    * APTonCD
    * Adobe Flash Player 10
    * Book Management Software
    * CHM Files
    * Converting PDF to PNG
    * Creating Backup of Downloaded Packages on CD
    * Desktop Widgets
    * Detailed Articles
    * Displaying Trash Network Home Computer Icon on Desktop
    * Displaying files and folder size wise
    * Fonts
    * Games
    * Gen Linux Newbies Tutorials
    * Google Applications for Linux
    * Google Picasa
    * Google earth
    * How TO
    * ImageMagick
    * KDE 4
    * Links
    * Long Articles
    * Make Ubuntu Look Like Mac OS X
    * Nautilus
    * PCMan File Manager
    * Reviews
    * Software Updates
    * Softwares
    * Tips
    * Transform Ubuntu 8.04 to look like Mac OS X
    * Troubleshooting
    * Tutorials
    * Ubuntu
    * Ubuntu 7.10
    * Ubuntu 7.10 Tutorials
    * Ubuntu 8.04
    * Ubuntu Customization
    * Ubuntu Tweaks
    * Ubuntu themes
    * Weather information on Ubuntu
    * gOS
    * iPhone
    * iPod

Get informed whenever new articles are posted in your Email :

Delivered by FeedBurner

Subscribe in Bloglines

Add to netvibes

Add to Google Reader or Homepage

Add to Google

Subscribe in NewsGator Online

Subscribe in Bloglines

Add to My AOL

Add to Bitty Browser

Add LINUX ON DESKTOP to Newsburst from CNET News.com

Add LINUX ON DESKTOP to Newsburst from CNET News.com

Subscribe in Rojo
Archives

    * May 2006
    * July 2006
    * August 2006
    * December 2006
    * January 2007
    * February 2007
    * March 2007
    * April 2007
    * May 2007
    * June 2007
    * July 2007
    * October 2007
    * November 2007
    * December 2007
    * January 2008
    * February 2008
    * March 2008
    * April 2008
    * May 2008

Site Meter

---

### Post by ELMIT on 2008-05-25
Thank you very much for this lengthy documents. 

I could however not spot the reason of my problem in it. Can you tell me which of the suggestion do you think would solve my problem and why.

Thanks

R.

---

### Post by andrew.46 on 2008-05-25
I have written the following guide just recently that deals with copying audio cds:

[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

and it works *very* reliably once set up carefully.

         Andrew

---

