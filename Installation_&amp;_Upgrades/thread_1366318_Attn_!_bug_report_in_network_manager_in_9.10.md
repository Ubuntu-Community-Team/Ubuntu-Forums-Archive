---
title: "Attn ! bug report in network manager in 9.10"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2009-12-28
hi all !
i am still new to this forum, hence taking the easy way out in making this post to report a problem that i have encountered in installing a broadband modem in 9.10. i would appreciate it if someone could pass it on to whoever fixes these bugs and provides updates (canonical ? ).
the modem in quesiton is the Huawei EC1260.
Although it is easily recognized by the network manager, i am just not able to connect to the internet.
after i have put in the user name and passwork (the telephone number) and try to connect , it gives me an error msg about lack of privileges etc.
basically, i am not able to connect the modem in 9.10. i believe that this is however supposed to be out of the box.
so please pass this on so that we may get an update to provide us some respite.
cheers!

---

### Post by phillw on 2009-12-28
Hi & welcome to the forums..

There are a few posts on the matter ... they seem to lead to this solution -->  [http://ubuntuforums.org/showpost.php?p=8255955](http://ubuntuforums.org/showpost.php?p=8255955)

So, I guess that should be your first stop.

Regards,

Phill.

---

### Post by AM_SOS on 2009-12-29
thanks philw!
ok so now i am going to ask a really amatuerish query.

actually i did come across this resolution page.

the problem is how to download and then install all these files :-(

e.g. when i click on 
[http://packages.ubuntu.com/karmic/wvdial](http://packages.ubuntu.com/karmic/wvdial)
i am directed to a page asking me to select a servers from one of regions.
but even here there are various archives / mirrors/ links. 
so which one to choose from ?
is it e.g. -
 kr.archive.ubuntu.com/ubuntu
or  th.archive.ubuntu.com/ubuntu
or  mirror.lupaworld.com/ubuntu
and so on ...

also once, one of these is saved, what do i do with them inside Ubuntu 9.10 ?

thanks !

---

### Post by tommcd on 2009-12-29
> **AM_SOS said:**
> 
the problem is how to download and then install all these files :-(
e.g. when i click on 
[http://packages.ubuntu.com/karmic/wvdial](http://packages.ubuntu.com/karmic/wvdial)
i am directed to a page asking me to select a servers from one of regions.
but even here there are various archives / mirrors/ links. 
so which one to choose from ?
is it e.g. -
 kr.archive.ubuntu.com/ubuntu
or  th.archive.ubuntu.com/ubuntu
or  mirror.lupaworld.com/ubuntu
and so on ...
also once, one of these is saved, what do i do with them inside Ubuntu 9.10 ?

When you go to: [http://packages.ubuntu.com/karmic/wvdial](http://packages.ubuntu.com/karmic/wvdial), select i386 at the bottom if you are using 32bit Ubuntu or amd64 if you have 64bit Ubuntu. Then select any mirror on the next page:
[http://packages.ubuntu.com/karmic/amd64/wvdial/download](http://packages.ubuntu.com/karmic/amd64/wvdial/download)
Download the package and place it in your home directory. Then open a terminal (applications > accessories > terminal).
 When you open a terminal, it should open to your home directory by default. You can check this by typing **pwd** and hit enter. It should report: /home/user_name (where user_name is your user name in Ubuntu when you login).  Then run:
```
sudo dpkg -i wvdial
```
and hit the TAB key. It should autocomplete the name of the wvdial package that ends with .deb. It will then ask you for your password. Once you provide your password the package will install. Do the same thing for any packages you need to install in this manner. After the packages are installed, you can delete them from your home directory if you wish to.

EDIT: You could also right-click on the package and it should offer to open it with the G-Debi Package Installer. This is a graphical tool for installing .deb packages. So either install it from the terminal using dpkg, or use the G-Debi Package Installer.

---

### Post by AM_SOS on 2009-12-30
hi all !
first a big thanks to you tommcd . i didn't have any difficulty in installing the packages. and yes i found the GUI interface installation method much more simpler :)
now you may recall that i was trying to install a CDMA broadband modem.
for this i was trying to configure the  wvdial  application. however, i have run up with some problems and although i can now get it to recognize the modem, i am still not able to connect and reach the final stage which displays for me the DNS server address etc.

first, when i make the changes in wvdial.conf , it doesn't allow me to save these changes. to work my way around this, i saved it as a separate file (Broadband_wvdial) on my desktop.

however, when i ran the   sudo wvdial   command i got the following messages at the end-

OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

i suspect that it is not even reading the file i have saved on my desktop as   Broadband_wvdial  . This is where i have put in all the relevant settings.
The reason is that the wvdial window that comes up when i type   gedit /etc/wvdial.conf   in a Terminal window says that it is a Read Only file and therefore i am forced to save it as another file on the desktop.
finally, i am not sure that i have installed the package files any particular order. i think i installed  wvdial  first and then the  base ,  extra  and  iconf  packages. perhaps this is the source of the problem?
desperately want to connect,
please help!

---

