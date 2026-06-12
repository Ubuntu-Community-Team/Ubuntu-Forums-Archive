---
title: "Using MS Windows workstation connected to Internet to download packages for Ubuntu"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by slavne on 2009-12-17
**Ubuntu Download Program for Windows ver 1.3/1.4**

**Motivation**: Ubuntu is prepared to download packages from Internet for both installation and update purposes. If your Ubuntu machine is not connected to Internet but you have access to Internet from MS Windows machine, then you possibly need a program Ubuntu Packages Downloader (shortly UPD). 

**Usage**: UPD program analyses the package that user wants (we can call it "main package") and performs automatic downloading on MS Windows machine. Downloaded packages can be transferred to Ubuntu machine either manually or over local network and then installed there.

**Operating system:** MS Windows XP Pro. Still it should be operable on other Windows flavors starting from MS Windows 2000. 

**Download UPD**: [http://rapidshare.com/files/321814042/upd.zip](http://rapidshare.com/files/321814042/upd.zip)

**Installation: **
  1) Download the UPD program.
  2) You are advised to check that MD5 signature of your upd.zip is 6a964671d6f8286ececc1d9874fd33c7. If using a Windows machine for MD5 calculation check you can do that by selecting the file upd.zip in TotalCommander, then activate command File / CreateCRCChecsums, then open the file upd.md5 to check the MD5 signature. Afterwards you can delete upd.md5
  3) Unzip the contents of archive in any Windows directory you like. That&#8217;s all.

**Starting UPD:** click twice to start.hta
 
**Short description of UPD: **
The program has two main screens. Here is how the First screen looks like:
[IMG]http://nesic.rs/UBUNTU/screen1.jpg[/IMG]

On _the First screen_ you minimally decide about a main package (say build-essential), choose an Ubuntu distribution the main package belongs to (say "jaunty"), a web download site closest to your destination (say "Serbia: RC ETF") and just press button "Next" on the right side. You can customize all this (see later in text).

After you pressed "Next", the First screen is lost, and some minimized screens are shown down at the taskbar; you must be PATIENT and wait for those and other program screens to finish; if you like you can click on them to activate them and see their contents (one is empty and the other shows progress (like "Reading Packages.*.main... Reading Packages.*restricted... Reading Packages.*.universe...Reading Packages.*.multiverse..."). So be waiting as long as it needs for the Second screen to emerge. 

_The Second screen_ looks like this:
[IMG]http://nesic.rs/UBUNTU/screen2.jpg[/IMG]

The Second screen is large and you could need to scroll down or up. In the Second screen you get the list of selected packages the UPD program thinks you need to download; it contains all depends and predepends packages along with your main package (build-essential). The size and number of the selected packages for download is estimated and presented below the list (see "Total size of selected packages" and "Total number of selected files"). You are free to deselect some or all of the selected packages by pressing Control-click on any of them; at the same time your currently selected total files size and number will be refreshed at the bottom of the list.

When you press the button "Download selected packages" the currently selected packages will be downloaded from the internet site to your local directory; those internet site and local directory were actually chosen at the First screen that we already have seen above. That process can last some time depending mostly on your Internet connection, but be PATIENT and wait for the completion popup message.

**Warning 1:** if Screen 2 does not appear for some time you certainly should click on minimized windows to see if you got some strange message; if everything is normal you just have to be PATIENT long enough for Screen 2 to appear. The reason for that is very nature of clumsy MS Windows system and HTA programming, as well ability of the program to run on older Windows versions. Anyway if MS Windows were any good we should not install our Ubuntu machines, should we? :wink:

**Warning 2:** if after the First screen you obtain a warning message: "A script on this page is causing Internet Explorer to run slowly. If it continues to run, your computer may become unresponsive. Do you want to abort the script?"
No, you should not abort the script - just press NO, and the beautiful Screen 2 will appear. Trust me on this.
Sometimes this message is not seen because you were working on some other windows and the message stays minimized at the taskbar; if in any doubt just click on applications windows at the taskbar to make sure they are visible and there is no message popup waiting for your action. 

To lessen the possibility of obtaining such distracting messages, please find the file ukidaDosadu.reg in the installation directory. Click twice on it to install the small registry correction. Still the notice could appear but with lesser possibility. 

**Using Screen 1 &#8211; more details:**
  - In the first line of checkboxes (Depends, Recommends, Suggests, Enhances), Depends is always checked, because those packages are the minimum to be installed for your package. Actually UPD is taking care to include both Depends and Predepends packages for your main package. The rest is up to you.
  - As you can see packages from all current Ubuntu distributions can be downloaded. 
  - In the package name you can enter one main package. Alternatively, I left the possibility to enter more then one package by checking "Regular exp." checkbox and using the regular expressions which are unfortunately Microsoft format (sorry of this ugly word, folks, won't happen again :-). For most users this comment means you can enter multiple packages like this, just be careful in typing:
(ldap-account-manager)|(ldap-auth-config)|(ldapscripts)|(slapd)|(ldap-utils)|(migrationtools)

Here is another example:
(cups)|(cupsys)|(cupsys-bsd)|(cupsys-client)|(cupsys-common)|(foomatic-.*)|(hal-cups-utils)

If you are not sure about the MS regular expression format, I recommend using only the first form presented above; if you make a mistake UPD will consider your typing as some strange packages and just
skip over them so you will loose precious packages and the later installation on Ubuntu machine after packages are copied there would miserably fail.

**Using Screen 2 &#8211; more details:**
  - First part is informative, like 
Starting package analysis: gnome [Recommends] [Suggests] [Enhances]   -->what is being analyzed

Notice: the existing package bf-utf-source has non-empty Depends [Recommends][Suggests][Enhances] line but I did not find any one of them in the Packages.* files:
   I analized this: di-packages-build | boot-floppies...        
-->notices anomalies found

Warning: the following packages are listed as necessary but they do not exist in Packages.* files (e.g. dpkg-dev has perl5 listed in Depends but there is no info on perl5): perlapi-5.10.0      
-->some packages are mentioned as dependant upon, but no information is found about their whereabouts.

- List of selected packages. You can manually deselect any selected package you like, or select some more, or both. Nice, isn't it?

- Some other warnings like this:
Warning - packages with potentially offensive names: libsexy2_0.1.11-2_i386  -->some proxies does not allow this package, so program warns you about that, and you should find your way to get it other way.

- The last part of Screen 2 is a great time saver in case you have some of the packages already downloaded and want the UPD to skip them automatically when the button "Download selected packages" is pressed. For that you have some very powerful options:

"Check if some of the selected packages are already downloaded in the directory"   ---> name the directory where you have some packages downloaded. If UPD have some package for download, it checks if that is already contained in the directory and skips that package.

"If necessary (copy | move | just look for) them into <download directory from Screen 1> and deselect them in the list above"  
----> if some package is selected in the list and found in the directory "check if some of ...", then the UPD program will skip the downloading of that particular package and either copy or move it into the downloading directory. If you selected "just look for" then the UPD will only deselect the package from the list above, as if you did it manually.

_Special feature 1:_ download directory specified in the First screen can contain some packages already downloaded. That case can emerge for example when previous downloads were interrupted from some reason. If there are some packages in the download directory, when the Second screen appear any package from download directory will be deselected from the list. That way UPD do not download again the same packages.

_Special feature 2:_ suppose your Ubuntu machine already have some packages installed, and you don't want those packages downloaded at the Windows machine. So, if you wish the UPD program to skip downloading those packages, do the following:
1) Issue the command in the Ubuntu machine: 
    dpkg -l >instaliraniPaketi.txt 
2) Move the instaliraniPaketi.txt from Ubuntu machine to Windows Internet machine in the UPD installation directory.
3) Next start of UPD will skip selecting any packages in the Second screen if those packages are properly installed on Ubuntu machine!

**Warranty:** none of course :P. I am actually turning my attention to hardware and microcontrollers projects these days; this small project is just a part time job for my amusement, for reminding of the good old days of administration and a great pleasure of sharing the benefit of this program with all of you guys from whom I have learned a lot of times! I am using this program in its fourth version and all my Ubuntu server installations of are done with the UPD so I don't see why it should not perform well for you too.

**Viruses: **yes I planted a few viruses inside to see you sweating, and one of my favorites does &#8220;FORMAT C:". No, people, do not worry, just joking. This is one of the reasons why I am giving you MD5 signature in this post. You trust me, don't you?  Just make your antivirus program relax if it pops up a security warning about this script. The script is safe. 

**Customizing UPD:** find the file config.txt in the installation directory. These lines can be customized at your preference and I suggest you do it one at a time to be sure you do it correctly or otherwise the program won&#8217;t work as expected:
....
const sFajlInstaliraniPaketi = "instaliraniPaketi.txt"   
----> predefined name of file containing dpkg &#8211;l listing from your Ubuntu machine (see above). You change it some other name if you like

const sFajlPaketiZaPreuzimanje = "paketiZaPreuzimanje.txt"  
----> log file containing all packages from the Second screen list, either selected or not.

const sFajlPaketiZaPreuzimanjeSel = "paketiZaPreuzimanjeSel.txt" 
---> log file containing packages from the Second screen list which are initially selected by the UPD.

sPolaznoOdrediste = "lib"    
-----> default download directory; if relative path is used, it is in the UPD installation directory.

sDirVecPreuzeti = "e:\ld\gnome"   
----> default directory in the Second Screen &#8220;Check if some of the packages are already downloaded in the directory&#8221;. If non existing, the field in the Second Screen will be empty. User can delete it or change it as he  wishes.

ubuntuVerzije = Array( _
	"dapper-backports", "dapper-proposed", "dapper-security", "dapper-updates", "dapper", _
	"hardy-backports", "hardy-proposed", "hardy-security", "hardy-updates", "hardy", _
	"intrepid-backports", "intrepid-proposed", "intrepid-security", "intrepid-updates", "intrepid", _
	"jaunty-backports", "jaunty-proposed", "jaunty-security", "jaunty-updates", "jaunty", _
	"karmic-backports", "karmic-proposed", "karmic-security", "karmic-updates", "karmic", _
	"lucid")  
-----> simply add new distribution under apostrophes here when it appears in Ubuntu site, but also do not forget to download the Packages.gz, unzip it and name it Packages.<distribution e.g. jaunty-backports>.<component e.g. main> Actually this manual download and unzip is not necessary because I gave UPD the ability to download the appropriate Packages.gz from Internet, unzip them and rename approprately; that ability however depends of you having the license for the program PowerArchiver Command Line from [http://www.powerarchiver.com;](http://www.powerarchiver.com;) if you happen to have that program, just download its files in the pe directory and the UPD will use it if it needs to; in that case you don&#8217;t need to download and decompress Packages.gz - the UPD will do that automatically for you. 

sPolazniSajt = "RC ETF"   
-----> default start value in the First screen for &#8220;Choose mirror site closest to your place&#8221; list. You have to type exactly what you see in the list entry you like, otherwise UPD won&#8217;t recognize your &#8220;inventiveness&#8221;. Apostrophes are must!

sPolaznaVer = "jaunty"  
------> default distribution in the First screen for &#8220;Ubuntu version&#8221; list. Type exactly the appropriate distribution from the "ubuntuVerzije" list. Do not forget apostrophes!

--------------------------------------------------------
So that's all, folks. What shall you do next, with all those packages? Well who knows?):P it served me well to incorporate those into APT hierarchical repository. There are other posts here how this can be done. Anyway, see you around. :guitar:

---

