---
title: "Problem removing prior application files"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by paulcan on 2013-02-09
[FONT=Arial][SIZE=2]I have a problem deleting a prior application.[/SIZE][/FONT][SIZE=2] 

 [/SIZE][FONT=Arial][SIZE=2]After updating Ubuntu to 12.10. I received a message some files could not be removed. When I subsequently tried to install “Wine” , the wine installation reported it could not install Wine until “libjack0” was removed.  Libjack0 a file associated with sound functions. [/SIZE][/FONT]

[FONT=Arial][SIZE=2]I have tried the Debian uninstall package manager, and "sudo dpkg -r program_name", [/SIZE][/FONT][FONT=Arial][SIZE=2]both[/SIZE][/FONT][FONT=Arial][SIZE=2] attempts[/SIZE][/FONT][FONT=Arial][SIZE=2] also failed.
[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Does anyone have other  suggestions on how to delete these files associated with libjack0?[/SIZE][/FONT]

---

### Post by ibjsb4 on 2013-02-09
You could try autoremove (#3).

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by paulcan on 2013-02-09
> **ibjsb4 said:**
> You could try autoremove (#3).

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

Thankyou, I will try this.

---

### Post by paulcan on 2013-02-09
> **ibjsb4 said:**
> You could try autoremove (#3).

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

I did try one of the commands on the page you directed me to, 

[FONT=Symbol][SIZE=2][FONT=Symbol]"·[FONT=Times New Roman][SIZE=1]                [/SIZE][/FONT][/FONT][/SIZE][/FONT]apt-get purge <package_name>  [FONT=Times New Roman][SIZE=2]This command completely removes a package and the associated configuration files. Configuration files residing in ~ are not usually affected by this command."[/SIZE][/FONT]
  
I found that even with an administrator account I had to preface the command with "SUDO". I learned the the term sudo elevates the permission level to owner. 

Thank you for the help.:p:p:p

---

### Post by ibjsb4 on 2013-02-09
Yes "sudo" is necessary.  There is also "dpkg" commands.

[http://www.ubuntugeek.com/reference-guideubuntu-package-management-using-dpkg.html](http://www.ubuntugeek.com/reference-guideubuntu-package-management-using-dpkg.html)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dpkg&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dpkg&as_qdr=all&sa=Google+Search&lang=en)

If this is solved

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

