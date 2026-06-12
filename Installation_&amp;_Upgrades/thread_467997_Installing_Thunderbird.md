---
title: "Installing Thunderbird"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by juice13610 on 2007-06-08
I am totally, 100% new to Linux.  I am using Ubuntu 7.04.

I am trying to install Thunderbird, but I have no clue how to install anything on a Linux machine.  I have downloaded the tar.gz archive and extracted the folder to my desktop.  Now what??

Thanks in advance!

---

### Post by NewJack on 2007-06-08
If you check in the repositories, you should see TB in there.  When you find it, just click on it and check the option "Mark for install".  Then click on the "Apply" button and it should install itself and any dependencies that is needed.  You can delete the tar.gz file since you don't need it.

---

### Post by phillife on 2007-06-10
Hi,

in ubuntu there is already Evolution, so why do ppl still install TB? I am very nw to Ubuntu infact my is just load an hour ago.

IF i load TB, can it use my outlook pst file as i check evolution and it cant.


Thanks

---

### Post by NewJack on 2007-06-13
phil, try this link as a start:

[http://kb.mozillazine.org/Import_.pst_files](http://kb.mozillazine.org/Import_.pst_files)

or try the following ( I found it here- [http://www.postneo.com/2005/02/26/thunderbird-shortcomings-outlook-import-support#comment-83533):](http://www.postneo.com/2005/02/26/thunderbird-shortcomings-outlook-import-support#comment-83533):)



To import outlook PST on Windows to Thunderbird on Linux, try the following.

1.)
Install Mozilla on the Windows PC where the .pst file resides.

2.)
Use Mozilla to import the .PST file. Mozilla will create a directory structure somewhere like:
C:\Documents and Settings\fred\Application Data\Mozilla\Profiles\default\hk2l1z6b.slt\Mail\Local Folders\Outlook Mail0.sbd

3.)
Install Thunderbird on Linux box. Create a folder named outlook_import in Thunderbird. Create another folder named dummy under outlook_import. This is needed because of the way folders and sub-folders are recognised by Thunderbird. You should now have a folder on Linux named something like the following.
/root/.thunderbird/4jkb6o2f.default/Mail/Local Folders/outlook_import.sbd

4.)
Then copy the sub-folders from Windowe under Mail\Local Folders\Outlook Mail0.sbd to Linux to Mail/Local Folders/outlook_import.sbd.

5.)
Stop and start Thunderbird. You should now be able to read your old .PST mail in Thunderbird.

6.)
Tell everyone else who is having this problem. There seem to be many comments out there.

---

### Post by geezerone on 2007-06-14
You may find [ [COLOR="Sienna"]this guide[/COLOR] ]("https://help.ubuntu.com/community/") useful.

Automatix is a handy way to install/uninstall software too.

---

### Post by warcriminal on 2007-06-14
There is an article at;

[http://www.goitexpert.com/entry.cfm?entry=Install-Thunderbird-on-UBUNTU](http://www.goitexpert.com/entry.cfm?entry=Install-Thunderbird-on-UBUNTU)

That shows you step by step how to install Thunderbird on UBUNTU.  There are screenshots there as well, and the same concept applies to other programs and applications.

---

### Post by matchstich on 2007-06-16
i went to the package manger on my 7.04 feisty . which i just installed today.

it shows thunderbird already installed. 

question: how do i find it. looked all thru the applications and it is not there.

went to main menu--not there .

thanks.

---

