---
title: "I cannot upgrade to gtk+ 2."
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by Hristian on 2007-06-04
Hello all.

I am trying to install f-prot on Ubuntu 7.04.  I have a problem because the system has only Gtk+ libs version 1.2.10 but the installation needs version 2.4.x or superior - see below.

How can one update to the newest version of gtk+?  When I update my system, it says it already has the newest version of gtk+.

Thanks.

Hristian

====== Terminal output =======

hristian@DELLi7500:~/xfprot-1.18$ sudo ./configure --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Using default value: 'sudo'

Autodetecting f-prot's install directory....please be patient
found: /usr/local/f-prot
Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for konsole.....Not found
Checking for xterm.....OK

Found unsupported Gtk+ libs version 1.2.10
I need version 2.4.x or superior.

Found Gtk+ libs version 2.10.11
Using Gtk+ 2.10.11 libs
Adding optimization statements to Makefile.in
Setting language to en_GB, you can override this with: --with-lang=xx_XX
Supported languages are:
de_DE
en_GB
es_ES
fr_FR
it_IT
pl_PL
pt_BR
hristian@DELLi7500:~/xfprot-1.18$ sudo make
cc -DIS_LINUX -DGTK_2_10 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -M xfprot-gtk.c TextViewWindow.c TextEditWindow.c AboutWindow.c TextCommon.c DialogWindow.c FileSelector.c mygtk.c mylib.c >> .depend
cc -DIS_LINUX -DGTK_2_10 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -c -o xfprot-gtk.o xfprot-gtk.c
cc -DIS_LINUX -DGTK_2_10 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -c -o TextViewWindow.o TextViewWindow.c
cc -DIS_LINUX -DGTK_2_10 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -c -o TextEditWindow.o TextEditWindow.c
cc -DIS_LINUX -DGTK_2_10 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -c -o AboutWindow.o AboutWindow.c
cc -DIS_LINUX -DGTK_2_10 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -c -o TextCommon.o TextCommon.c
cc -DIS_LINUX -DGTK_2_10 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -c -o DialogWindow.o DialogWindow.c
cc -DIS_LINUX -DGTK_2_10 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -c -o FileSelector.o FileSelector.c
cc -DIS_LINUX -DGTK_2_10 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DL_window_create -DL_table_create -DL_frame_create_on_table -DL_default_text_box_create_on_table -DL_button_create_on_table -DL_radio_create_on_table -DL_textpad_create -DL_check_create_on_table -DL_default_label_create_on_table -DL_textpad_create_on_table -DL_default_button_box_create_on_table -DL_button_create_in_container -DL_radio_create -DL_check_create -DL_button_create -DL_button_box_create_on_table -DL_statusbar_create_on_table -DL_main_loop -DL_main_menu_create -DL_attach_to_table -DL_window_close -DL_progressbar_create_on_table -DL_progress_destroy -DL_progressbar_create -DL_progress_timeout -DL_about_callback -DL_text_box_create -DL_label_create -DL_frame_create -DL_my_gtk_entry_set_text  -c -o mygtk.o mygtk.c
cc -DIS_LINUX -DGTK_2_10 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DL_msg -DL_err_msg -DL_xsnprintf -DL_xcalloc -DL_xalloc_die -DL_xmake_message -DL_xmalloc -DL_xpclose_nostdin -DL_xfclose_nostdin -DL_xgetcwd -DL_xpopen -DL_xopen_die -DL_trim -DL_get_line_from_file -DL_xconcat_path_file -DL_xrealloc -DL_xstrncat -DL_xchmod -DL_xchown -DL_xchdir -DL_xputs -DL_xmkdir -DL_last_char_is -DL_xstrdup  -DL_xfgetc_nbuf -DL_xfree -DL_xstrlen -c -o mylib.o mylib.c
cc -DIS_LINUX -DGTK_2_10 -DNDEBUG -O3 -pipe -fomit-frame-pointer -fno-builtin -std=gnu99 -include i18n/en_GB.h -include mylib.h -include mygtk.h -include config.h -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -o xfprot-gtk xfprot-gtk.o TextViewWindow.o TextEditWindow.o AboutWindow.o TextCommon.o DialogWindow.o FileSelector.o mygtk.o mylib.o

hristian@DELLi7500:~/xfprot-1.18$ sudo check install
sudo: check: command not found

hristian@DELLi7500:~/xfprot-1.18$ sudo apt-get install libgtk-devReading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libgtk1.2-dev instead of libgtk-dev
libgtk1.2-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  lockfile-progs liblockfile1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Hristian on 2007-06-04
Hello all.

1. My problem was somewhere else.  Although the message in my previous note shows that gtk+ is an older version (1.x instead of 2.4.x, there is apparently newer versions libraries installed already unter Ubuntu 7.04 as well.  They get displayed as 2.10.x in the message.

2. I reinstalled xf-Prot from the /. directory instead of my home directory where the Terminal opens the window automatically, and now the xf-Prot works just fine.

3. I have both xf-Prot and AVG-Free installed, but neither run as resident anti-virus programs.  When I open the test virus file from xf-Prot, neither detected.  xf-Prot detects it only on a scan run, and AVG-Free does not detect it at all on a scan run.

4. I am playing with Ubuntu to see what one of the most used Linux distributions can do.  I can say that it is  stable.  Since I started a week ago, I never had a break-up of the system.  But I must also say that it is a b..ch of a system trying to add software, or to find software in the first place.  And all the dependencies are a nightmare.  For example when I deinstalled some USB installations, it also started listed HAL and other OS related files.  Now I know to say CANCEL for the specific installations.  But before I had no idea.  I reinstalled Ubuntu for the second time.  Ubuntu should automatically say, "Not allowed to do that because these files are OS needed files!"

I still wonder why people want to use Ubuntu at all - or any Linux version for that matter (I played with openSuse as well), when one can buy Win XP for 80 something bucks on amazon.de.  I do not understand the advantages at all of a Linux OS.  Perhaps as I continue working with and learn different Linux systems, I will learn the advantages of using any Linux system whatsoever.  Perhaps the server versions are more usefull for running DB applications.  But for example when one needs specific applications to run on the server, as they do in my woman's clinic, which are only built for Windows, tough luck.  Can only run with Windows installed in VMware environment, but then, hey, I will just install Windows.

I feel really sorry that there is no alternative to Windows, which installs and runs Window programs, which reads and writes NTFS files automatically, and which is user friendly.   Perhaps the Linux designers should only use novices to test their distributions.  Until now I see the Linux designers test their own systems, and even more, on environments which are either virtual or very specific.  Ran into so much crap with TWiki plugins for example.  Plugins and updates to plugins were designed without even testing them in a normal environment.  They are defect on arrival...

Sincerely,

Hristian

---

### Post by zvacet on 2007-06-04
>  I do not understand the advantages at all of a Linux OS

Say hello to maleware when it comes to you.And this is just one thing.

---

### Post by Hristian on 2007-06-04
Hi Zvacet.  First, please do believe me, I am not a Microsoft lover.  I had an Amiga back in '87, and it kicked even then today's Win XP's ***.  And at school I worked with Solaris and, I guess, another OS that I already forgot what is called, which used to transfer the work-loads between workstations - something that even today's Windows cannot do.  But we also have to be honest and reflective.

1. If you mean malware and spyware, my home XP PC is protected to the teeth and all for free.

2. If you mean male-ware, I would only say hello to my own... :-)

3. Did you ever think that your Linux machine could be a nest of viruses?  You would never know it, and you would send all the infected emails and documents to your pals.  And none of them would know it either, until it would be too late for some of them and most who use Windows.  And let us face it, there are some nasty Unix viruses floating around that would bring your machine to its knees.  I still do not understand why the Linux distributions do not have a built-in anti-virus program that works.  The one that I saw built-in like the clam-something, I could never configure it in Ubuntu, at least until now.

4. Like I said, I just bought two XP Prof. packages for about 86 Euros a piece on amazon.de.  A bargain.  Yes, indeed, I hate myself a bit for contributing to Gate's grosse wealth, but I will have two machines running beautifully without any f..k headaches that I get with the Linux distributions.

5. And let us face it, there are some big problems, I perceive, in the way the Linux distributions are engineered and tested.  One of my degrees was in Applied Computer Science, and I did a lot of Software Engineering.  Although 20 years ago, the rules still apply.  The Linux distributions today are not so great at all.  They are not tested correctly, they are not implemented correctly, and they are not updated correctly. I saw the Ubuntu forums and they are filled up with calls for help, which many can never be answered.  I do realize that most of the Linux distributions are done by people on their free time.  And I really can appreciate the effort and motivation of these people.  I thank all of them from the bottom of my heart for trying to provide an alternative to Microsoft and for supporting the open source environment.

But still, there has to be some focus and a reason for why people do so much work.  For example, to meet some of the reasons why Amiga, Mac and other systems were never able to take market share from Microsoft (one reason or the other): (1) provide 100% Microsoft file compatibility FAT & NTFS; (2) allow programs designed for Microsoft OSes to run 100% the same way on the Linux or other OSes, (3) provide a user-friendly system.  This should be the focus of the Linux community and not to provide Linux distributions from which everyone gets a one big f..g headache from installing and maintaining.  Because this will only convince people even more to move to Microsoft.  And trust me, Linux patriotism like any patriotism is a very dangerous thing, like from Nazi Germany to the big **** in Iraq where people go freely to die for nothing...  Would one also want to sacrifice himself on the altar of a not-so-good Linux distribution?  I am exaggerating, of course, but just to make a point.

In the end, I still do not understand the benefits of a Linux distribution.  Financially is not cheaper (considering that my time is money), security-wise is not better (in Windows I can use free anti-virus, free anti-spyware, free firewall, etc., and I mean the best on the market), in software-variety is not better, and in time-savings for sure is not better.  I still miss my Amiga 1000...the thing would not crash if you hit it with a hammer, and it would install any software designed for it without a glitch.  Yeah, I understand, it was just one hardware platform.  Oh well...  Maybe we should not have a 1001 Linux distributions but only two or three.  ANd he same with the hardware.  Focus and conquer, and not divide and lose...

---

### Post by zvacet on 2007-06-05
> If you mean malware and spyware, my home XP PC is protected to the teeth and all for free.

Meaning your anti-virus,anti-spyware anti..... doesn´t detect it.That doesn´t mean they are not there.

> . Did you ever think that your Linux machine could be a nest of viruses?

No,because I can install some anti-virus program if I feel like it.Let say Avast or some other available.

>  Maybe we should not have a 1001 Linux distributions but only two or three

Good side of linux is that anybody with knowlage,interest and free time can contribute.I agree that way linux can be in bad situation because many people in same time work on the same thing and that is waste of time resources ,energy....

I tryed Windows and Linux and I like Linux better,but I´m not linux preacher.I think that everybody is free to make choices.If somebody decide to use something different of linux I will not try to make him/her to change decision.

---

