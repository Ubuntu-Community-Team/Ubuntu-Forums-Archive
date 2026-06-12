---
title: "Vim-full installation on 9.10"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by tosandip on 2010-03-09
Hi Gurus,

I have a problem installing vim on ubuntu 9.10. I tried following command and it results in following error.

sudo apt-get install vim-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vim-full

Please help me in setting up vim on 9.10

Regards
Sandip

---

### Post by thebigob on 2010-03-09
Its just called vim

I know its odd as there is already vim installed but as you say this is no the full vim.

Just type:

sudo apt-get install vim

this should replace your current vim with the full version

---

### Post by tosandip on 2010-03-10
No That either is not helping. I already tried  that.

Is there any issue with the apt-get then? apt-get not able to download any packages then?

I'm using dell 1564 laptops with broadcom Wireless hardware, Driver is downloaded from broadcom.com. Firefox is able to browse internet.

Please suggest

Regards
Sandip

---

### Post by thebigob on 2010-03-10
Could be something to do with your sources.

If you have a browser working you can try downloading directly from [URL="http://packages.ubuntu.com/search?keywords=vim-full"]here.
[/URL] 
Hope this helps let me know how you get on.

---

### Post by tosandip on 2010-03-10
> **thebigob said:**
> Could be something to do with your sources.

If you have a browser working you can try downloading directly from [URL="http://packages.ubuntu.com/search?keywords=vim-full"]here.
[/URL] 
Hope this helps let me know how you get on.


Can you also let me know how we can check for sources on ubuntu 9.10?

Regards

---

### Post by thebigob on 2010-03-10
cat /etc/apt/sources.list

will show you what your sources are.

The red section in the link I posted showed you represents which source is required for this package.

what you are looking for in this is:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe

These are not enabled by default however do appear in the file.

To enable these you simply uncomment them by removing the # at the start of the line.

---

### Post by tosandip on 2010-03-11
> **thebigob said:**
> cat /etc/apt/sources.list

will show you what your sources are.

The red section in the link I posted showed you represents which source is required for this package.

what you are looking for in this is:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe

These are not enabled by default however do appear in the file.

To enable these you simply uncomment them by removing the # at the start of the line.

I checked my sources.list file.. I found following lines

deb [http://in.archive.ubuntu.com/ubuntu/]("http://gb.archive.ubuntu.com/ubuntu/") karmic universe
deb-src [http://in.archive.ubuntu.com/ubuntu/]("http://gb.archive.ubuntu.com/ubuntu/") karmic universe

I have added lines provided by you to this sources.list file. But still packages are not getting downloaded.

I tries all following packages
vim
vim-full
vim-gnome

None was downloaded.

Regarding downloading a package from link you had provided, I was able to download vim*.deb file. Now I have no Idea how to install this package.


Please help.

Regards
Sandip

---

### Post by thebigob on 2010-03-11
You should be able to double click the .deb file and click install.
 
Otherwise you can use the following command:
 
sudo dpkg -i package_file.deb
 
package_file.deb being the full path and file name. eg /tmp/vim.deb

---

### Post by tosandip on 2010-03-12
> **thebigob said:**
> You should be able to double click the .deb file and click install.
 
Otherwise you can use the following command:
 
sudo dpkg -i package_file.deb
 
package_file.deb being the full path and file name. eg /tmp/vim.deb


Thanks the thebigob.

I'm able to get vim installation with your support (BTW I'm a fan of vim and can not imagine a OS without Vim) , But then for sure my apt-get need some fix.
I also wanted to Install csh/tcsh packages.. Which again are not getting downloaded automatically.

Synaptic package manager is also not showing these packages either. But anyway this seems like a separate topic.

Thanks for all the help

Regards
Sandip

---

### Post by thebigob on 2010-03-12
> **tosandip said:**
> Thanks the thebigob.

I'm able to get vim installation with your support (BTW I'm a fan of vim and can not imagine a OS without Vim) , But then for sure my apt-get need some fix.
I also wanted to Install csh/tcsh packages.. Which again are not getting downloaded automatically.

Synaptic package manager is also not showing these packages either. But anyway this seems like a separate topic.

Thanks for all the help

Regards
Sandip

Glad I could help and you got it sorted.

Good luck with getting synaptic sorted. I am sure there will be lots of threads on this matter.

---

### Post by pragya on 2010-12-23
Hi,

As posted above, I am trying to install vim using the .deb method. But I am always getting the error after I double click on the .deb file:


Error: Dependency is not satisfiable: vim-gui-common (= 1:7.0-035+1ubuntu5.2~dapper1)

What does this error mean??

Also, I tried the other sources.list method but that is also not working properly. It gives the error that some of the files are not downloaded and then it stops.

I would be really grateful if someone helps me out. I need to work with text files that have around 1Gb size. If there is any other good text editor, then please tell me that also.

Thanks

---

