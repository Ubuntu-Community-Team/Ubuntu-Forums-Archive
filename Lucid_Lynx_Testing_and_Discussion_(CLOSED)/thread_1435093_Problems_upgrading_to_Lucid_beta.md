---
title: "Problems upgrading to Lucid beta"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mhenriday on 2010-03-21
These last couple of days, I've been trying to upgrade from my 64-bit Karmic setup, but after performing «Alt + F2», and «upgrade-manager -d» to start the installation process, the latter comes to a grinding halt with the following error message :
> Kunde inte beräkna uppgraderingen [Could not calculate the upgrade]

An unresolvable problem occurred while calculating the upgrade:
Försöker att installera svartlistade versionen [Attempting to install the black-listed version] &#8221;openoffice.org-filter-binfilter_1:3.2.0~rc4-1ubuntu1&#8243;

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

Om inte någon av dessa stämmer så rapportera detta fel mot paketet &#8221;update-manager&#8221; och inkludera filerna i /var/log/dist-upgrade/ i felrapporten. [If none of these is the case, report this «update-manager» package bug and include the files in /var/log/dist-upgrade/ in the bug report]
and the procedure was rolled back.

On another forum, I was advised to run 
```
sudo aptitude update

sudo aptitude safe-upgrade

sudo update-manager -d
```
in a terminal, after which the following appeared there :
> Läser paketlistor [Reading package lists]&#8230; Färdig [Finished]
Bygger beroendeträd [Building dependency tree]
Läser tillståndsinformation [Reading permissions information]&#8230; Färdig
Läser utökad tillståndsinformation [Reading expanded permissions information]
Initierar pakettillstånd [Initiating package permissions]&#8230; Färdig
Följande paket kommer att TAS BORT [The following packages will be REMOVED]:
openoffice.org-help-zh-cn{u} openoffice.org-help-zh-tw{u}
openoffice.org-l10n-zh-cn{u} openoffice.org-l10n-zh-tw{u}

[I fail to understand what these Chinese language OOo help files have to do with the Lucid installation, but that's another matter....]

0 paket uppgraderade [0 packages upgraded], 0 nyinstallerade [0 newly installed]. 4 att ta bort [4 to be removed] och 0 inte uppgraderade [and 0 not upgraded].
Behöver hämta 0B arkiv. [Need to fetch 0B archive] Efter uppackning kommer 78,5MB diskplats att frigöras. [After extraction will 78.5MB disk space be freed]
Vill du fortsätta? [Do you wish to continue ?] [Y/n/?] Y
(Läser databasen [Reading the data base] &#8230; 182473 filer och kataloger  installerade [files and catalogues installed].)
Tar bort [Removing] openoffice.org-help-zh-cn &#8230;
Tar bort openoffice.org-help-zh-tw &#8230;
Tar bort openoffice.org-l10n-zh-cn &#8230;
Tar bort openoffice.org-l10n-zh-tw &#8230;
Läser paketlistor&#8230; Färdig
Bygger beroendeträd
Läser tillståndsinformation&#8230; Färdig
Läser utökad tillståndsinformation
Initierar pakettillstånd&#8230; Färdig
Skriver utökad tillståndsinformation&#8230; Färdig

mhenriday@mhenriday-baerbar:~$ sudo update-manager -d

extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg'

So far so good, but after about fem minutes I once again receive the error message concerning the attempt «to install the black-listed version &#8221;openoffice.org-filter-binfilter_1:3.2.0~rc4-1ubuntu1&#8243;» och the installation process is rolled back. Any suggestions as to a workaround ?&#8230;

Henri

---

### Post by phillw on 2010-03-21
Hi,

you would be better of asking on the Lucid forum --> [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

I'm not sure where the 64bit is up to.

My only 'hint' would be to remove Open Office, upgrade & re-install it. But I'd strongly suggest you ask over on the Lucid area.

safe-upgrade leaves the old files behind, you *may* well need to point your repo's over to Lucid.

```

sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

```


Regards,

Phill.

---

### Post by mhenriday on 2010-03-21
**Phill**, thanks for your speedy reply ! Given the nature of the error message, I had been considering uninstalling **OOo** and your suggestion pushed me over the line - I uninstalled and was then able to upgrade to **Lucid** via «Alt + F2» and «upgrade-manager -d». I can't call the upgrade painless - after installation, a lot of files had to be repaired (a very long process !) before I could successfully boot into **Lucid**, but once that was done, I had no trouble re-installing the Ubuntuised version of **OpenOffice** and everything now seems to be hunky-dory. But I think I'll wait until **beta 2** is released before upgrading my main box....

Henri

---

### Post by arvindshes on 2010-03-22
Thank you Phil. Your suggestion worked out.

I am just not able to wait till April 29.

---

### Post by mhenriday on 2010-03-23
As is, alas, my wont, I was a bit premature in assigning a «Solved» tag (which I've now removed) to this thread ; as can be seen from my [**_[COLOR="Blue"]post to this thread[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=9015377#post9015377://") and to [**_[COLOR="Blue"]another one[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=9015547"), which I took the liberty of initiating, I'm not quite out of the woods yet....

Henri

---

