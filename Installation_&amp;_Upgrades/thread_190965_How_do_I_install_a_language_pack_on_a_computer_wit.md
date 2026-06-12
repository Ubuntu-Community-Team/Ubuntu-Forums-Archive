---
title: "How do I install a language pack on a computer with no internet access?"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by midorigin on 2006-06-06
How do I install a language pack on a computer with no internet access?

The language packs don't appear to be included on the Desktop CD. I have the ability to download them using another computer and transfer them, but I don't know which of the many *language-pack-** and *language-support-** packages I need to download.

The following are a few examples of the many packages listed:[LIST]
[*]*language-pack-gnome-XX-base*
[*]*language-pack-gnome-XX*
[*]*language-pack-XX-base*
[*]*language-pack-XX*
[*]*language-support-XX*
[/LIST]
I don't know how these are organized, if there's one main package I need or if I should install them all.

I also realize that these probably have many dependencies. How can I download a package AND the dependencies it will need for installation on a computer without internet access?

Thanks a ton. I'm setting up Ubuntu on a few hundred donated computers destined for Turkey, and the children will very much appreciate being able to understand them. :)

---

### Post by Sef on 2006-06-06
> How do I install a language pack on a computer with no internet access?

1) Get a computer with access.

2) []("http://packages.ubuntu.com")

3) Go to the Dapper Section 

4) then translations

5) find packages you are looking for

6) download and burn to a cd

7) install on net-less system

---

### Post by midorigin on 2006-06-07
***My working solution, posted for anyone else who needs help:***

(Adapted from [this guide]("https://wiki.ubuntu.com/AptMoveHowto"))

[COLOR="DarkRed"]Disclaimer: I really don't know what I'm doing, so follow these instructions at your own risk. They worked for me, but I'm not smart enough to know if I've broken anything in the process. I also have a hunch this probably relies on doing this on a newly-installed system. I think it makes the assumption that the system you're preparing the CD on has pretty much the same stuff installed as the one you're making the CD for, so be warned that you might get some dependency errors if your system's been changed a lot.[/COLOR]

[LIST=1]
[*]Install apt-move (Universe) if you haven't already: ```
sudo apt-get install apt-move
``` Open apt-move configuration ```
sudo gedit /etc/apt-move.conf
``` and change the line *COPYONLY=no* to ```
COPYONLY=yes
```
[*]Packages installed using apt-get are cached in */var/cache/apt/archives*. We're going to use this as a staging area for everything to be put on to the CD. First, clear the cache so we can start fresh and include only what we want. [COLOR="DarkRed"](Caution, this deletes stuff. Is there a better way to do this?)[/COLOR] ```
sudo apt-get clean
```
[*]Now go to Gnome's language settings and check the box by any languages you want on the CD. Go ahead and install them; by doing this we're making apt-get cache everything we need in */var/cache/apt/archives*. You can go back and uninstall the languages when we're all done.
[*]Use apt-move to create a local repository in */mirrors/debian*. (For more information, check out [the guide]("https://wiki.ubuntu.com/AptMoveHowto")) First create the file *~/myapt.conf* ```
gedit ~/myapt.conf
``` and paste the following inside: ```
APT::FTPArchive::Release {
Origin "APT-Move";
Label "APT-Move";
Suite "dapper";
Codename "dapper";
Architectures "i386";
Components "main restricted";
Description "Ubuntu Languages CD";
};
``` Then run the following commands: (NOTE: This requires you to have a GPGKey. Follow the instructions [here]("https://wiki.ubuntu.com/GnuPrivacyGuardHowto").) ```
sudo -s
rm -rf /mirrors/debian
apt-move -d dapper update
cd /mirrors/debian
apt-ftparchive packages pool/main/ \
  | gzip -9c > dists/dapper/main/binary-i386/Packages.gz
apt-ftparchive packages pool/restricted/ \
  | gzip -9c > dists/dapper/restricted/binary-i386/Packages.gz
rm dists/dapper/Release
apt-ftparchive -c ~/myapt.conf release dists/dapper/ > Release
mv Release dists/dapper/Release
``` Enter the following and provide your GPGKey password when asked: ```
gpg -bao dists/dapper/Release.gpg dists/dapper/Release
``` Continuing... ```
rm -rf .apt-move
mkdir .disk
echo Ubuntu-Languages `date +%Y-%m-%d` > .disk/info
gpg --export -a "*[COLOR="Magenta"]YOUR GPG NAME[/COLOR]*" > public.key
exit
```
[*]To make an ISO image for burning the CD: ```
mkisofs -r -A "Ubuntu Languages `date +%Y%m%d`" -o ubuntu-languages.iso \
  /mirrors/debian
``` Burn it with you favorite cd-burning software.
[*]On any computer you want to install to from the CD, stick the CD in and then run the following command to tell apt to trust the new repository: ```
apt-key add /cdrom/public.key
```
[*]In Synaptic, choose *Edit > 'Add Cdrom'*. Install what you need from the CD's repository, then when you're done and take the CD out, be sure to remove the repository from apt/Synaptic's list so it doesn't get confused trying to find it later.
[/LIST]

Hope this helped.

---

