---
title: "No upgrades are available from Oneiric"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by loungeliz on 2013-10-19
When I   [SIZE=2]>  **[FONT=courier new]sudo apt-get upgrade[/FONT]** [/SIZE] after an update, I get "no upgrades available."  When I   [SIZE=2]**[FONT=courier new]> sudo apt-get dist-upgrade[/FONT]**[/SIZE], I get nothing.  If I run the update manager GUI, I get the same results.  Is there something set somewhere that is not allowing me to see 12.04, 12.10, 13.04, 13.10, and 14.04 versions on this box?

-- da Lizard

---

### Post by oldos2er on 2013-10-19
11.10 Oneiric is no longer supported, hence the "no upgrades available." While it's possible to [upgrade an EOL version]("https://help.ubuntu.com/community/EOLUpgrades"), a fresh install may give you fewer problems in the long run.

---

### Post by Frogs Hair on 2013-10-19
Hello and Welcome 

11.10 has been  unsupported since May and the repositories are closed  . You have two options , one being and end of life upgrade and the other would be a clean installation of a newer version. I would choose the second option. 12.04 LTS has the longest support period.  

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)    

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Bashing-om on 2013-10-19
loungeliz; Hi ! Welcome to the orum .
> 
 Is there something set somewhere that is not allowing me to see 12.04, 12.10, 13.04, 13.10, and 14.04 versions on this box?

Yes, one must alter the sources list to point to the old archive and then update. 
But the process to update from an End Of Life version is a long one, updating must be done version to next version to next version to the current version.
Here is the tutorial to alter your system to do the on-line upgrade:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

