---
title: "Newbie: Want to install 400 packages"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by brucenduane on 2006-06-05
Thanks for your help and reading this

Just installed Dapper Drake 6.06 on third machine of six

Did an upgrade on first machine from Breezy 5.10 to Dapper 6.06
All 6 PCs are different makes and hardware and all have/had Breezy installed.

I found it faster to just install Dapper Drake from LiveCD except:
I need to put ~400 packages on the machines beyond the base Dapper install.
This list is all the diffences between the base install and my running Dapper system.

The list of packages is edited from the text list made by  "dpkg -l > pkg.txt"

Is there a program which can extract the second string from this file and do a
"sudo apt-get install $string"

or a command like  
"cat pkg.txt | extract second string | sudo apt-get install $str"

The list includes libs and may match existing packages so the command/program would need to continue on error or empty install.   Disk space is not a problem >40 gigs free.

Thanks for your help and for reading this.

-Bruce.

---

### Post by llamakc on 2006-06-05
dpkg --get-selections < /path/to/package.list

I think. Shoot, lemme double check that one.

---

### Post by llamakc on 2006-06-05
I believe you do:

dpkg --get-selections > package.list

Which gets the packages in a manner that the next command understands.

This would be on the 2nd, target machine after scp'ing over package.list to it.

dpkg --set-selections < package.list

But I forget what you do next. Sorry, beer kicking in.

---

### Post by brucenduane on 2006-06-05
Thanks for the quick reply.

How do I extract the package name from the second column of the output from the
dpkg -l  command into a file?   I assume I just can not feed it the output file directly.

-Bruce.

---

### Post by brucenduane on 2006-06-06
What I have figured out so far.
Use dpkg to get list example:   $ dpkg -l > pkglist.txt

Produce two lists   full_pkglist.txt   and  new_pkglist.txt

Use gedit to remove the first header lines of the files

Reduce lists to just the package names
$ awk '{ print $2 }' full_pkglist.txt > full.txt
$ awk '{ print $2 }' new_pkglist.txt > new.txt

Get the difference in the package lists

$ diff full.txt new.txt > diflst.txt

extract the ones from the full.txt that need to be installed

$ cat diflst.txt | grep ">" > to_be_installed.txt
$ awk '{ print $2 "   Install" }' to_be_installed.txt > install_pkgs.txt

extract the ones from the new.txt that need to be removed

$ cat diflst.txt | grep "<" > to_be_removed.txt
$ awk '{ print $2 "   Remove" }' to_be_removed.txt > remove_pkgs.txt

Thats where I am so far.  I have not tested the two package lists with dpkg yet.
Need to go to bed now, will try again in the morning.

-Bruce.

---

### Post by llamakc on 2006-06-06
dpkg --get-selections and --set-selections handle this for you the same. I'd try the one to set the package list, EDIT it, then scp it to the new machine and get a-workin'.

Good luck.

---

### Post by brucenduane on 2006-06-06
Thanks IIamake,

It took me 6 hours to do the 400 packages by hand and only 5 minutes automated
plus the download time.  A whole lot less effort!!!!

Correction to my above notes!
The valid commands to add with the "awk" command are:
                 install    hold   deinstall   purge      (# all in lower case )

The example of file for dpkg would be:   example_pkg.txt

bibletime   install
amoke  deinstall
xine  purge
[eof]

The file would install bibletime, remove amoke, and purge xine.

It is executed with the following 2 commands in sequence

$ sudo dpkg --set-selection < example_pkg.txt
$ sudo dselect install

Answer the question on the deselect command an have fun!!!

Thanks again  IIamake for your help.
-Bruce.

---

### Post by brucenduane on 2006-06-06
Thanks**[SIZE="4"] IImakc[/SIZE]**

Sorry for the name misspell.
-Bruce.

---

### Post by brucenduane on 2006-06-06
Let me try this one more time with a working keyboard!!

Thanks **[SIZE="5"]Ilamakc[/SIZE]**

-Bruce.

---

### Post by llamakc on 2006-06-06
Good to hear.

---

