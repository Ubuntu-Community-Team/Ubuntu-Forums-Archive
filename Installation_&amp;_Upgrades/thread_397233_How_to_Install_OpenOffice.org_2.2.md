---
title: "How to: Install OpenOffice.org 2.2"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by alanandhispc on 2007-03-30
Hi,

To install openoffice 2.2, you can follow the guide found [here]("http://www.ubuntuforums.org/showpost.php?p=1945243&postcount=29")

Just make sure you install alien first. (sudo aptitude install alien)

Certain looks like it is running even quicker than 2.1, which is nice...

> **sgla1 said:**
> I have installed open office 2.1 on edgy as follows:

1) download OO 2.1 from openoffice.org
2) remove the Ubuntu version of open office -- it's broken anyway 
```
 dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove
sudo apt-get autoremove
```
3) convert the downloaded openoffice files from rpm to deb:
```
cd dir_where_you_extracted_the_OO_compressed_file
cd RPMS
sudo alien --scripts --keep-version *.rpm
```
4) install the new version of openoffice:
```
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb

```

This should work for dapper as well; ymmv :-)

Reference: [http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370)

Steve G


Alan

---

### Post by wgtripp on 2007-03-31
I just followed the instructions which worked beautifully for 2.2.  Thanks for the question and answer!  GT

---

### Post by silkstone on 2007-04-03
Just done the same and it works great.  (Just make a coffee while it converts all the .rpm files to .deb. ;) )

Thanks to sgla1 for the original and alan for the link.

---

### Post by silkstone on 2007-04-03
Having installed everything, I assume it's OK to delete the original tar file and all the RPM files, and just keep the DEB files converted by Alien in case you want to reinstall?

---

### Post by SickJedi on 2007-04-03
When downloading from openoffice.org I'm asked for username and password. What are they? I regitered there but I can't use that username and pass to download.

---

### Post by mpadams on 2007-04-03
I did a 7.04 beta install and did some updates and noticed 2.2 is installed. The method described here should be reserved or modified for older distros.

---

### Post by silkstone on 2007-04-03
Yes, I believe that OO 2.2 is installed with Feisty, but that is still beta. The method here is for those using Dapper or Edgy.

---

### Post by podcastrant.com on 2007-04-07
I'm totally new to all of this, so I'm not sure if I did it right.

I'm assuming the first line of code that has a bunch of "|" separations is supposed to be typed as one line of code ending in "-y".  If this is true, when I do it I get this, "E: Invalid operation openoffice.org".

If anyone knows what I did wrong, please help.

Thanks in advance.

---

### Post by eekfonky on 2007-05-17
followed the instructions but can't find where to open the installed apps. they're not in: Application -> Office. Any ideas?

---

### Post by Hagar Delest on 2007-05-17
> **mpadams said:**
> The method described here should be reserved or modified for older distros.
Scan the forum and you'll find that this Ubuntu version (Feisty) of OOo is really bad. Much more bugs than previous versions. Better install the official one.

[QUOTE=eekfonky]followed the instructions but can't find where to open the installed apps. they're not in: Application -> Office.[/QUOTE]
Are you sure you've installed the desktop-integration package ? If so, had you removed all the OOo packages delivered with Ubuntu ?

---

### Post by faust99 on 2007-05-18
> **Hagar de l'Est said:**
> Scan the forum and you'll find that this Ubuntu version (Feisty) of OOo is really bad. Much more bugs than previous versions. Better install the official one.



Thanks for this-it worked great and has fixed the bugs.

---

### Post by ukripper on 2007-05-19
Worked like charm. Alien is cool.

PS: While installing Alien if you are being asked to insert CD then you have to amend sourcelist and comment out ## CDROM in very first line in the sourcelist

---

### Post by WestCoastSuccess on 2007-05-20
I'm a little confused by Step 3 - why cd into where you downloaded the file, only to immediately cd to RPMS? Am I missing something (sorry, relative newbie!)?

Cheers,

Martin

---

### Post by WestCoastSuccess on 2007-05-20
Sorry - the file hadn't finished downloading when I tried it, hence no RPMS folder - please disregard my previous post!

Martin

---

### Post by donnellymp on 2007-07-05
Ah, yes, now that OO is broken in Gutsy, this method might be the best way forward. And then you can get the updates right from OO itself, not Ubuntu.

---

