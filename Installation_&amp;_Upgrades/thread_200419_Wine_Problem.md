---
title: "Wine Problem"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by raffytaffy on 2006-06-20
I instaled wine...i try to run it in terminal..and this is what i get

raf@raf-ubuntu64:~$ wine
wine: error while loading shared libraries: libntdll.so: cannot open shared object file: No such file or directory

what can i do.....btw heres some info
raf@raf-ubuntu64:~$ whereis libntdll.so
libntdll: /usr/local/lib/libntdll.so

---

### Post by scr on 2006-06-20
You could try to add the directory /usr/local/lib to the file /etc/ld.so.conf as it states in 'man ldconfig'. After inserting that line of text into that file, try running 'sudo ldconfig'.

Hope it helps.

---

### Post by raffytaffy on 2006-06-20
dont have such a file lol

raf@raf-ubuntu64:~$ man idconfig
No manual entry for idconfig
raf@raf-ubuntu64:~$ idconfig
bash: idconfig: command not found
raf@raf-ubuntu64:~$ sudo idconfig
sudo: idconfig: command not found

---

### Post by Slippy1979 on 2006-06-21
that's an L not an I. LDCONFIG.

---

### Post by scr on 2006-06-21
it doesn't exist as default, so just create it, add the line and run **ldconfig**. Oh, and keep your fingers crossed

---

### Post by bodhi.zazen on 2006-06-22
You still have work to do.

First you need to configure wine. See here:

[http://www.ubuntuforums.org/showthread.php?t=149585](http://www.ubuntuforums.org/showthread.php?t=149585)

I have used winetools with mixed results.

I personally use sidenet, it depends on what software you want/need to run. Check the apps database on the wine site for details of what software you are trying to run.

Sidenet:

[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

The downloads at the bottem of the page are what you want. for example: wine-config-sidenet-1.9.1.tgz.  In my experience no two versions of wine/wine tools or wine/sidenet configuration comninations are equal. You will need to experiment.

Wine:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

next you need to configure wine and possibly some DLL's, Run the command winecfg.

Last to run a program type:
wine <name of program>

It can be very complicated, you should start at wine HQ -> search the application data base, follow instructions, watch for an exact match in versions of wine.

BTW: what windows software are you trying to run?

---

### Post by raffytaffy on 2006-06-22
I was runing IE6 and Yahelite on wine.....IE bcse some websites require it...yahelite...bcse i like to chat in peace lol

---

### Post by bodhi.zazen on 2006-06-22
Sidenet, either of the two more recent versions, will have IE6 up and running in short order. I do not know about Yahelite.

Most likely, after IE6 is running, you will type

wine <name_of_yahelite_install_program> (use the full path to the install program such as /mnt/cdrom/install.exe or whatever your situation).

Also wine does not always recognize your cd rom device as it should . Easiset way is to irst mount the cd. then in the /home/user/dosdevices directory manually type a link [ln -s /mnt/cdrom/ f:] (do not use an already existing drive letter)

Then type wine f:install_program_name.exe

Then to run type wine /home/user/Path_to_to_fake_c_drive/Program\ Files/Yahelite/Yahelite.exe

you can add an alias to your ~/.bashrc (alias yahe='wine /home/user/Path_to_to_fake_c_drive/Program\ Files/Yahelite/Yahelite.exe'

then to run type yahe in a terminal.

Or add an icon to your desktop (depends on desktop).

---

