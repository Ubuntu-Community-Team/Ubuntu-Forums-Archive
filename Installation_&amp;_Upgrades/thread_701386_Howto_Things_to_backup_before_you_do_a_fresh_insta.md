---
title: "Howto: Things to backup before you do a fresh install"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by justleen on 2008-02-19
I know there already some info and posts on this, but I've found myself (again) in a position where I need (well...want, really) to reinstall Linux.
I do this quite often actually, and i use several personal reminders and some basic backup of installed files and settings.. 

I thought it might be handy for other users if i wrote down "my backup procedure" since this can save a lot of time when reinstalling.
I've got no pretentions this is a bullet proof method, but its meant to provide some handy pointers, not as a backup procedure to be safe when your systems crashes.
.
I'll be assuming you have no seperate partitions, just one disk or partiton with "/" mounted on it.
Creating seperate partions for /home and /usr and others  can be very handy, but I know most people do not have a setup like this.

**1. Where you should backup:**
if you have a "default" system installed, you will most likely have 1 partition which is mounted on "/".
this means, if your format this drive, everything will be lost.
In order to save your files you'll need a seperate parition (or a cd/usb stick) to backup to so they survive the format.
Personally, I have a 5gb fat32 partition labeled "Backup". Since i have a dual boot system, this is handy since both windows and linux can realibly write to this partition.
if you do have free unpartitioned space on your disk, its a good idea to create an extra partition for backup purposes. If you do not have extra space or partitions, you can write the backups to your windows partition using the NTFS-3g driver/tool.
If you have one big disk for linux and nothing else, i advise to backup to CD or USB.
In the case you have none of the above, your could resize your disk with gparted to create space.
A thing i've done in the past is to turn my swap off, delete the swap partition, and create a backup partition in there. This is not ideal, but hey, your gonna reinstall anyway Smile


**2. what you should backup:**
[COLOR="Red"]/etc/[/COLOR] => all of the config file are here. create a backup of this for the sole reason that if you do reinstall, and find some things are not working as before, you can simply take one file from this archive and place it back to its original location. Your xconf.org for example. If you reinstall, fix your GPU drivers,and find its not working as before it might be very handy to place the old xorg.conf back.
You could just pick the files you need from /etc, but since the folder is tiny when compressed (1,1MB on my system), i just tar the whole folder.

[COLOR="Red"]/var/cache/apt/archives[/COLOR] => all of the downloaded and newly installed packages are here. Creating a backup of this folder can be quite a time saver if you did a reinstall, since you wont have to download all the files again. FOr example, I installed LAMP, next install i dont have download all the packages, i can just use dpkg -i to reinstall the LAMP server

[COLOR="Red"]/home/leen/.mozilla/firefox/obvjotfm.default[/COLOR] => you firefox settings. Keep in mind, mozilla creates a random folder name for each install where it stores your setting. Do NOT archive this folder, but the contents. When restoring, place the contents in the new random folder
(the "obvjotfm.default" in this example....)

[COLOR="Red"]/home/leen/.applicationname[/COLOR] => any user settings for an application will most likely be in a "hidden" folder in your home folder. /home/leen/.gaim/ will contain all of my gaim settings. simply restoring the folder after a new install will setup gaim again.
Offcourse, if the application itself is not yet installed, you can restore the folders, but it will have no effect - your only restoring settings.

[COLOR="Red"]/home/[/COLOR] => if you modified any profile files,backup those as well!!
for example, /home/leen/{.bashrc, .profile, .netrc, .nzbperlrc} etc
if you have enough space, create a backup of the whole /home.
[COLOR="Red"]
source files for applications [/COLOR]=> if you installed any apps from source, make sure you keep the tarball, otherwise you will have to download them again.

_concerning source installs_: personally,i try to keep a install history and install log of any application I installed from source. This will help set me up any applications a lot faster next time round.
For example, when I'm finished installing an application, I type "history" at the command line, and copy paste from the start of the install to the end of the install - this give me a record of every command i typed to get it working. I use[ "elog"]("http://midas.psi.ch/elog/") to save all this in, but a email to your self with install details can save you hours! furter i keep a record of anything other then commands, to keep a list of other things i did to install (copies of guides and howto's, edited lines/files, etc).
I've found over the years that it can be VERY handy to keep track of changes this way. It can be a real pain when you cant find this one HowTo you've used to install this or that, or that you cant remember this one flag for ./configure which made things work on your system.
One last note: Make sure you backup your own howto's! (yes, i have deleted my own howtos!)


**3.creating archives:**
once you know what you wanna keep for you new install, your ready to create the archives.
There's two way for this, the GUI, and the commandline.
The GUI speaks for itself I think. right click what you wantto archive,and select "Create Archive"
YOu can then open the archive, and drag more files into it. Or you can create seperate archives.
This method can be quite click-intensive..

The second option is trough the commandline with tar.
An advantage of this is, is that you can easily create a backup script to run every now and then based on the command you used...
Tar comes default on most normal *NIX installations, so there is no need to install any package to use this.
Tar is fairly easy to use (though you wouldnt say if you open the manpage Wink )
Basicly, what i do is this:

tar -czvfp /media/backup/backup.tar.gz /home/leen/.mozilla/firefox/*.default/ /home/leen/Desktop/ /home/leen/.gaim/ /home/leen/.netrc /home/leen/.profile /home/leen/.bashrc /home/leen/.nzbperlrc

what this does:
-c: create archive
-z: use gzip (the tar file is compressed with gzip)
-v: verbose output - i like to see stuff happening on my screen
-f: use a file. this might sounds weird, but tar was intended for use with tape drive. in this case we
explicitly have to mention that we want to use a file for the output
-p: preserve. this will preserve the right of the ownership (read/write/excute)

the syntax after this is <outfile> <path to add> <path to add> <path to add> <path to add>
the output file doenst havce to end with tar.gz, but its handy, that way you know what kind of file it is..(.tgz is commonly used as well)
so you can just add more paths to add to the archive.

tar has about a zillion other option you can use, one that can prove very handy is the "--exclude=PATTERN"
say, you want your whole home folder to be backed up, but not your movies folder.
/media/backup/ $ tar -czvf backup.tar.gz --exclude="movies" /home/leen/

Notice i'm not backing up my /etc/ with this command!
I try not to stuff everything in one file.. i keep my /etc/ in a seperate tarball, since when you extract the tar ball, it will overwrite everything. which in /etc/ is not what i want..
I keep the backups labelled like "etc_backup.tar.gz" "home_backup.." "var_backup.."



**4. restoring archives:**
say you want to restore the files to you home folder, this is as simple as:
cd (just plain cd <enter> you will change into your home folder)
tar -zxvf /media/backup/backup.tar.gz

this will extract the tar ball contents to your home folder.. (and other folders you included in the archive!)


NOTE: i do not use tar on the ,deb files! i just copy those to another partition!
cp /var/cache/apt/archives/* /media/software/
once i 'm done installing the OS, i just go into /media/software and do a:
dpkg -i ./*

this will install all the .deb files in that folder. 
[COLOR="Red"]**NOTE!!!**[/COLOR]
This will install ALL the packages you have dowloaded and installed!
If you dont want all packages, do them one-by-one!
Further more, this is not a replacement for the update functionality!! When i did this on a cleanly installed system, i got everything up and running just fine. However, the update-manager found 13 broken packages, which it fixed upon the next update. This method of installing previous installed .deb files is only meant to prevent you donwloading all the packages again!

obviously, any src installs will have to be done by hand.. But you kept a install guide, right? Smile


Well.. thats about it really. for me this means i can do an install, untar some tarballs, install the updates and any packages i installed through apt, and have everything back up and running well under an hour (i did a test drive on a clean install, fully updated with LAMP installed, took me just ovr 35 mins..)


I hope this usefull to some of you, enjoy!

---

### Post by K.Mandla on 2008-02-19
Moved to Installation and Upgrades.

---

### Post by pitje on 2008-02-20
hey, thx for the useful pointers! :)

I knew some of your suggestions, but others will come in very handy when I do my next install

which, in the way I sometimes try to tinker with my system, won't be too far in the future :P

---

### Post by DonDodge on 2008-02-20
I'm looking at a (another) fresh install to correct a nividia/envy driver problem.  Last night I downloaded hundreds of megabytes of system and program updates with Update Manager. Can all these update files, now stored in /var/cache/apt/archives, be reinstalled in such a way that Update Manager will be satisfied that the system is updated?

---

### Post by justleen on 2008-02-22
> **DonDodge said:**
> I'm looking at a (another) fresh install to correct a nividia/envy driver problem.  Last night I downloaded hundreds of megabytes of system and program updates with Update Manager. Can all these update files, now stored in /var/cache/apt/archives, be reinstalled in such a way that Update Manager will be satisfied that the system is updated?


The update manager will not be entirly satified with the state your system is in..

I had a fresh install, did an update, installed some extra packages. then i copied the apt-cache dir to a backup drive.

after a fresh install i did a dpkg -i * in the backup folder. (on the train, with no network)
everything was installed without any error, and everything worked just fine
The next time i was on a network, 13 broken packages where found (out of 253). i just chose "fix broken" and 10 secs later this was resolved.

So, in my experience, it works just fine, you just need to run a fix broken afterwards.

---

### Post by the badger on 2008-03-23
hey,[COLOR="Sienna"] this is great!![/COLOR] i've been poking around all morning trying to find a way to compress my /home (it's grown) so i can get it backed-up. 
however, i'm still new to the game so i'm going to ask if someone can help me better understand the following...
> tar -czvfp /media/backup/backup.tar.gz /home/leen/.mozilla/firefox/*.default/ /home/leen/Desktop/ /home/leen/.gaim/ /home/leen/.netrc /home/leen/.profile /home/leen/.bashrc /home/leen/.nzbperlrc
[COLOR="Sienna"]/media/backup/backup.tar.gz[/COLOR]:
when i'm creating this new file/folder(?) which part is the location? can i make a .tar.gz file of my /home *inside* my /home folder (so i can see how big it is before i decide what's all going on the backup dvd).

[COLOR="Sienna"]/home/leen/.mozilla/firefox/*.default[/COLOR]:
instead of specifying, i'm just going to go for the whole shebang, so can i specify [COLOR="Sienna"]/home/badger[/COLOR] or is it [COLOR="Sienna"]/home/badger/*[/COLOR] or something else?

many many thanks.

---

