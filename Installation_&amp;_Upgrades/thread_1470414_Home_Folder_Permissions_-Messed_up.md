---
title: "Home Folder Permissions -Messed up"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by rahduke on 2010-05-02
This is kind of confusing to explain but I'll do my best. So I have a small SSD that I use as my OS partition and I keep my Home folder on a separate drive.

I decided to do a clean install of 10.04 from 9.10, So I burnt a live CD wiped my SSD and installed a clean version. I chose the user name rahduke. Upon 1st boot I edited my fstab to point to my old home folder (rahduke) on my separate partition.

fstab entry
" /dev/sdb1 /home ext3 auto,users,rw 0 0 "

Magically the Home folder merged or something, it just worked! It was really cool

Now that I've done that, I am having all sorts of vague permission problems, double clicking executable files in nautilus does not give me the option to open them in terminal or run them, it will only launch gedit. I have checked the preferences of nautilus and it's set correctly. I've also chmod +x, chown'd chmod 775 etc etc. Nothing works, so that is problem 1.

My next problem is when running .sh, ./configure, autogen etc in terminal:

1a. Covergloobus: [http://gloobus.wordpress.com/](http://gloobus.wordpress.com/) trying to compile the latest version of Covergloobus for lucid. When getting to step 5 (./autogen --prefix=/usr/) I get an error "./autogen.sh: 5: ./configure: Permission denied". It doesn't matter what I do to the files or folder or how I run the autogen command I get the permission denied error.

1b. Veetle: When attempting to install the Veetle Plugin [http://www.veetle.com/](http://www.veetle.com/) I am able to run the .sh and install. I have confirmed the plugin is in the necessary folder however, Firefox does not recognize that Veetle has installed, neither does Chrome.

[http://pastebin.com/sXCUCuQu](http://pastebin.com/sXCUCuQu)

thats the output of the permissions I have as a user


There are others too,hopefully this enough for now. 

Please help me!

---

