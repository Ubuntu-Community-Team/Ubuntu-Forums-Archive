---
title: "Evolution and Empathy issues"
date: 2009-07-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Aries K on 2009-07-11
Hi, anyone having a problem with Evolution? Mine does not start, it will show it loading in the taskbar and then dissapear.

Second, after the recent update in the daily PPA with Empathy has anyone lost the ability for Adium message styles? Thanks in advance.

---

### Post by wayne_cat on 2009-07-11
evolution starts without a problem on my system (latest updates

Try to start evolution from gnome-termial ... maybe you can see an error.

edit:

this is what is looks like wen I start it from a terminal

```
rschmitt@macbook:/$ evolution
** (evolution:3480): DEBUG: mailto URL command: evolution %s
** (evolution:3480): DEBUG: mailto URL program: evolution
```

 ... than evolution starts.

---

### Post by Aries K on 2009-07-11
When I attempt to run it from Terminal I get:

```
ar@acer-desktop:~$ /usr/bin/evolution
addressbook_migrate (0.0.0)
*** glibc detected *** /usr/bin/evolution: double free or corruption (!prev): 0x0000000001725c60 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f737475ddc8]
/lib/libc.so.6(cfree+0x76)[0x7f7374760386]
/usr/lib/libedataserver-1.2.so.11[0x7f737a9ff7c9]
/usr/lib/libedataserver-1.2.so.11(e_categories_get_list+0x1c)[0x7f737a9ffc5c]
/usr/lib/evolution/2.28/plugins/liborg-gnome-calendar-weather.so(e_plugin_lib_enable+0x22)[0x7f7366881a32]
/usr/lib/evolution/2.28/libeutil.so.0[0x7f737e926638]
/usr/lib/evolution/2.28/libeutil.so.0[0x7f737e92688a]
/usr/lib/evolution/2.28/libeutil.so.0(e_event_emit+0xa2)[0x7f737e91cdf2]
/usr/lib/evolution/2.28/components/libevolution-calendar.so(migrate_calendars+0x2f9)[0x7f736b673f99]
/usr/lib/evolution/2.28/components/libevolution-calendar.so[0x7f736b600b3f]
/usr/lib/evolution/2.28/libeshell.so.0(GNOME_Evolution_Component_upgradeFromVersion+0x74)[0x7f73802c7a64]
/usr/bin/evolution[0x40e7ad]
/usr/bin/evolution[0x40ee6e]
/usr/bin/evolution[0x40ef8f]
/usr/bin/evolution[0x416725]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x22e)[0x7f7374a939fe]
/usr/lib/libglib-2.0.so.0[0x7f7374a973c8]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a5)[0x7f7374a97825]
/usr/lib/libbonobo-2.so.0(bonobo_main+0x46)[0x7f7378d4e796]
/usr/bin/evolution[0x416c84]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f73747045e6]
/usr/bin/evolution[0x40b3d9]
======= Memory map: ========
00400000-00420000 r-xp 00000000 08:01 11064                              /usr/bin/evolution
00620000-00621000 r--p 00020000 08:01 11064                              /usr/bin/evolution
00621000-00625000 rw-p 00021000 08:01 11064                              /usr/bin/evolution
01538000-01777000 rw-p 00000000 00:00 0                                  [heap]
7f7360000000-7f7360021000 rw-p 00000000 00:00 0 
7f7360021000-7f7364000000 ---p 00000000 00:00 0 
7f7366035000-7f736604f000 r-xp 00000000 08:01 7718                       /lib/libgcc_s.so.1
7f736604f000-7f736624e000 ---p 0001a000 08:01 7718                       /lib/libgcc_s.so.1
7f736624e000-7f736624f000 r--p 00019000 08:01 7718                       /lib/libgcc_s.so.1
7f736624f000-7f7366250000 rw-p 0001a000 08:01 7718                       /lib/libgcc_s.so.1
7f7366250000-7f7366259000 r-xp 00000000 08:01 9846                       /usr/lib/libproxy.so.0.0.0
7f7366259000-7f7366459000 ---p 00009000 08:01 9846                       /usr/lib/libproxy.so.0.0.0
7f7366459000-7f736645a000 r--p 00009000 08:01 9846                       /usr/lib/libproxy.so.0.0.0
7f736645a000-7f736645b000 rw-p 0000a000 08:01 9846                       /usr/lib/libproxy.so.0.0.0
7f736645b000-7f7366460000 r-xp 00000000 08:01 35551                      /usr/lib/libsoup-gnome-2.4.so.1.2.0
7f7366460000-7f736665f000 ---p 00005000 08:01 35551                      /usr/lib/libsoup-gnome-2.4.so.1.2.0
7f736665f000-7f7366660000 r--p 00004000 08:01 35551                      /usr/lib/libsoup-gnome-2.4.so.1.2.0
7f7366660000-7f7366661000 rw-p 00005000 08:01 35551                      /usr/lib/libsoup-gnome-2.4.so.1.2.0
7f7366661000-7f736667b000 r-xp 00000000 08:01 25196                      /usr/lib/libgweather.so.1.4.5
7f736667b000-7f736687b000 ---p 0001a000 08:01 25196                      /usr/lib/libgweather.so.1.4.5
7f736687b000-7f736687c000 r--p 0001a000 08:01 25196                      /usr/lib/libgweather.so.1.4.5
7f736687c000-7f736687d000 rw-p 0001b000 08:01 25196                      /usr/lib/libgweather.so.1.4.5
7f736687d000-7f7366883000 r-xp 00000000 08:01 262777                     /usr/lib/evolution/2.28/plugins/liborg-gnome-calendar-weather.so
7f7366883000-7f7366a82000 ---p 00006000 08:01 262777                     /usr/lib/evolution/2.28/plugins/liborg-gnome-calendar-weather.so
7f7366a82000-7f7366a83000 r--p 00005000 08:01 262777                     /usr/lib/evolution/2.28/plugins/liborg-gnome-calendar-weather.so
7f7366a83000-7f7366a84000 rw-p 00006000 08:01 262777                     /usr/lib/evolution/2.28/plugins/liborg-gnome-calendar-weather.so
7f7366a84000-7f7366a87000 r-xp 00000000 08:01 262815                     /usr/lib/evolution/2.28/plugins/liborg-gnome-bogo-junk-plugin.so
7f7366a87000-7f7366c87000 ---p 00003000 08:01 262815                     /usr/lib/evolution/2.28/plugins/liborg-gnome-bogo-junk-plugin.so
7f7366c87000-7f7366c88000 r--p 00003000 08:01 262815                     /usr/lib/evolution/2.28/plugins/liborg-gnome-bogo-junk-plugin.so
7f7366c88000-7f7366c89000 rw-p 00004000 08:01 262815                     /usr/lib/evolution/2.28/plugins/liborg-gnome-bogo-junk-plugin.so
7f7366c89000-7f7366d4b000 r-xp 00000000 08:01 23961                      /usr/lib/libgstreamer-0.10.so.0.20.0
7f7366d4b000-7f7366f4b000 ---p 000c2000 08:01 23961                      /usr/lib/libgstreamer-0.10.so.0.20.0
7f7366f4b000-7f7366f4f000 r--p 000c2000 08:01 23961                      /usr/lib/libgstreamer-0.10.so.0.20.0
7f7366f4f000-7f7366f51000 rw-p 000c6000 08:01 23961                      /usr/lib/libgstreamer-0.10.so.0.20.0
7f7366f51000-7f7366f52000 rw-p 00000000 00:00 0 
7f7366f52000-7f7366f55000 r-xp 00000000 08:01 262853                     /usr/lib/evolution/2.28/plugins/liborg-gnome-audio-inline.so
7f7366f55000-7f7367154000 ---p 00003000 08:01 262853                     /usr/lib/evolution/2.28/plugins/liborg-gnome-audio-inline.so
7f7367154000-7f7367155000 r--p 00002000 08:01 262853                     /usr/lib/evolution/2.28/plugins/liborg-gnome-audio-inline.so
7f7367155000-7f7367156000 rw-p 00003000 08:01 262853                     /usr/lib/evolution/2.28/plugins/liborg-gnome-audio-inline.so
7f7367156000-7f7367159000 r-xp 00000000 08:01 262880                     /usr/lib/evolution/2.28/plugins/liborg-gnome-prefer-plain.so
7f7367159000-7f7367358000 ---p 00003000 08:01 262880                     /usr/lib/evolution/2.28/plugins/liborg-gnome-prefer-plain.so
7f7367358000-7f7367359000 r--p 00002000 08:01 262880                     /usr/lib/evolution/2.28/plugins/liborg-gnome-prefer-plain.so
7f7367359000-7f736735a000 rw-p 00003000 08:01 262880                     /usr/lib/evolution/2.28/plugins/liborg-gnome-prefer-plain.so
7f736735a000-7f7367372000 r-xp 00000000 08:01 262779                     /usr/lib/evolution/2.28/plugins/liborg-gnome-itip-formatter.so
7f7367372000-7f7367572000 ---p 00018000 08:01 262779                     /usr/lib/evolution/2.28/plugins/liborg-gnome-itip-formatter.so
7f7367572000-7f7367573000 r--p 00018000 08:01 262779                     /usr/lib/evolution/2.28/plugins/liborg-gnome-itip-formatter.so
7f7367573000-7f7367574000 rw-p 00019000 08:01 262779                     /usr/lib/evolution/2.28/plugins/liborg-gnome-itip-formatter.so
7f7367574000-7f7367577000 r-xp 00000000 08:01 262885                     /usr/lib/evolution/2.28/plugins/liborg-gnome-vcard-inline.so
7f7367577000-7f7367776000 ---p 00003000 08:01 262885                     /usr/lib/evolution/2.28/plugins/liborg-gnome-vcard-inline.so
7f7367776000-7f7367777000 r--p 00002000 08:01 262885                     /usr/lib/evolution/2.28/plugins/liborg-gnome-vcard-inline.so
7f7367777000-7f7367778000 rw-p 00003000 08:01 262885                     /usr/lib/evolution/2.28/plugins/liborg-gnome-vcard-inline.so
7f7367778000-7f73677d2000 r-xp 00000000 08:01 26402                      /usr/lib/nss/libnssckbi.so
7f73677d2000-7f73679d1000 ---p 0005a000 08:01 26402                      /usr/lib/nss/libnssckbi.so
7f73679d1000-7f73679df000 r--p 00059000 08:01 26402                      /usr/lib/nss/libnssckbi.so
7f73679df000-7f73679e7000 rw-p 00067000 08:01 26402                      /usr/lib/nss/libnssckbi.so
7f73679e7000-7f7367a48000 r-xp 00000000 08:01 26396                      /usr/lib/nss/libfreebl3.so
7f7367a48000-7f7367c48000 ---p 00061000 08:01 26396                      /usr/lib/nss/libfreebl3.so
7f7367c48000-7f7367c49000 r--p 00061000 08:01 26396                      /usr/lib/nss/libfreebl3.so
7f7367c49000-7f7367c4a000 rw-p 00062000 08:01 26396                      /usr/lib/nss/libfreebl3.so
7f7367c4a000-7f7367c4e000 rw-p 00000000 00:00 0 
7f7367c4e000-7f7367c74000 r-xp 00000000 08:01 26400                      /usr/lib/nss/libnssdbm3.so
7f7367c74000-7f7367e74000 ---p 00026000 08:01 26400                      /usr/lib/nss/libnssdbm3.so
7f7367e74000-7f7367e75000 r--p 00026000 08:01 26400                      /usr/lib/nss/libnssdbm3.so
7f7367e75000-7f7367e76000 rw-p 00027000 08:01 26400                      /usr/lib/nss/libnssdbm3.so
7f7367e76000-7f7367eb2000 r-xp 00000000 08:01 26398                 Aborted (core dumped)

```

---

### Post by wayne_cat on 2009-07-11
Aries,

could you please check the libc6 version:

```
root@macbook:~# dpkg -l | grep libc6
ii  libc6                                          2.9-9ubuntu2                               GNU C Library: Shared libraries
ii  libc6-dev                                      2.9-9ubuntu2                               GNU C Library: Development Libraries and Hea
ii  libc6-i686                                     2.9-9ubuntu2                               GNU C Library: Shared libraries [i686 optimi
root@macbook:~# 

```Do you have another user on your system? Does it also crash if you log on with a different users?

---

### Post by Aries K on 2009-07-11
I get this:

```
ar@acer-desktop:~$ dpkg -l | grep libc6
ii  libc6                                      2.9-9ubuntu2                               GNU C Library: Shared libraries
ii  libc6-dev                                  2.9-9ubuntu2                               GNU C Library: Development Libraries and Hea
ii  libc6-i386                                 2.9-9ubuntu2                               GNU C Library: 32bit shared libraries for AM
ar@acer-desktop:~$ 

```

No, I made a "test" user previously and it worked fine, so I can log on as another user.

---

### Post by wayne_cat on 2009-07-11
I had this error:

```
*** glibc detected *** /usr/bin/evolution: double free or corruption (!prev):
```on Jauty ... but a libc6 update solved it. We are using the same libc6 version ... so this is something different ... Maybe you should create a launchpad bug report.

---

### Post by Aries K on 2009-07-11
> **wayne_cat said:**
> I had this error:

```
*** glibc detected *** /usr/bin/evolution: double free or corruption (!prev):
```on Jauty ... but a libc6 update solved it. We are using the same libc6 version ... so this is something different ... Maybe you should create a launchpad bug report.

I don't know if this has anything to do with it or not but my Karmic is an upgrade from Jaunty. The install went successfully though, just thought I'd throw that in there.

---

### Post by wayne_cat on 2009-07-12
try to move the .evolution folder to .evolution.orig .... does evolution start after this?

edit: evolution should start with the "settings screen" ... your old mails are not lost. You just have to delete the new "generated" .evolution folder
and move the "old" folder back with
```

mv .evolution.orig .evolution
```

---

### Post by Aries K on 2009-07-12
> **wayne_cat said:**
> try to move the .evolution folder to .evolution.orig .... does evolution start after this?

edit: evolution should start with the "settings screen" ... your old mails are not lost. You just have to delete the new "generated" .evolution folder
and move the "old" folder back with
```

mv .evolution.orig .evolution
```

Where are these folders located or can this be done in a command? Oh yeah thanks for your help btw.

---

### Post by wayne_cat on 2009-07-12
Aries,

the .evolution folder is in your home folder. So please try this in a gnome-termial

```
cd ~/

tar -cpvf .evolution .evolution.backup.tar

mv .evolution evolution.orig
```now ... try to start evolution. After the test you can recover your evolution settings with:

```
cd ~/
mv .evolution.orig evolution
```the line


edit: I'm offline now ... It is 06:30 in the morning here ... have to sleep a little bit ... maybe you should wait until other users come with tips / tricks

```
tar -cpvf .evolution evolution.backup.tar
```create a backup in your home folder .. just to be sure ;)

---

### Post by Aries K on 2009-07-12
Was I supposed to put /home/user/.evolution? I got this:

```
ar@acer-desktop:~$ cd ~/
ar@acer-desktop:~$ tar -cpvf .evolution .evolution.backup.tar
tar: .evolution: Cannot open: Is a directory
tar: Error is not recoverable: exiting now
ar@acer-desktop:~$ mv .evolution evolution.orig
mv: cannot move `.evolution' to `evolution.orig/.evolution': Directory not empty
ar@acer-desktop:~$ 
```

EDIT: I see it made the Evolution.org folder but still no workie. I also misred your question about "Evolution working under another user". I thought you were asking "Was I able to log on as another user in general". To answer that question, no it does not work not matter what user I am logged in as. Thanks for your help though, didn't mean to keep you up.

---

### Post by Craigy90 on 2009-07-12
> **Aries K said:**
> Was I supposed to put /home/user/.evolution? I got this:

```
ar@acer-desktop:~$ cd ~/
ar@acer-desktop:~$ tar -cpvf .evolution .evolution.backup.tar
tar: .evolution: Cannot open: Is a directory
tar: Error is not recoverable: exiting now
ar@acer-desktop:~$ mv .evolution evolution.orig
mv: cannot move `.evolution' to `evolution.orig/.evolution': Directory not empty
ar@acer-desktop:~$ 
```

EDIT: I see it made the Evolution.org folder but still no workie. I also misred your question about "Evolution working under another user". I thought you were asking "Was I able to log on as another user in general". To answer that question, no it does not work not matter what user I am logged in as. Thanks for your help though, didn't mean to keep you up.

Well, first of all, when using the tar command, the name of the output file goes first after the options. So the command would be

```
tar -cpvf .evolution.backup.tar .evolution
```

Note that this creates a hidden tar file. Now make sure that .evolution.orig does not exist, and do

```
mv .evolution .evolution.orig
```

---

### Post by yelo3 on 2009-07-12
Adium themes must be placed in this directory: $HOME/.local/share/adium/message-styles/

---

### Post by wayne_cat on 2009-07-12
Aries,

sorry .. I made a mistake ... see the post from Craigy90.

It does not work with a "fresh and clean" user? ... I think you should file a bug report.

---

### Post by Aries K on 2009-07-12
Tried Craigy90's method and it still does not fire up. I filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/398486](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/398486)

> Adium themes must be placed in this directory: $HOME/.local/share/adium/message-styles/

yelo3, which Empathy are you running the one from the repositories or the one from the daily ppa? I tried that method but there is no option at all in the daily ppa Empathy (2.27.4) to select an Adium theme while the older (2.27.3) has an option for Adium styles which I find unusual. Am I missing something?

---

### Post by wayne_cat on 2009-07-12
Thank you for filing the bug report.

---

### Post by tahina on 2009-07-13
> **Aries K said:**
> Tried Craigy90's method and it still does not fire up. I filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/398486](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/398486)

I had the same error, I think. In the bug-thread on launchpad they said to get a [Valgrind log]("https://wiki.ubuntu.com/Valgrind"). For me, logging starting of evolution with Valgrind somehow fixes the issue, so I am unable to log the error...

```
sudo apt-get install valgrind
```
```
G_SLICE=always-malloc G_DEBUG=gc-friendly  valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log evolution
```

EDIT:
**[COLOR="Red"]Now, with evolution 2.27.4-0ubuntu1 I don't get the error anymore.[/COLOR]**

---

### Post by Aries K on 2009-07-13
Thanks but I fixed the problem by reinstalling Karmic, all is well so far. I needed an E-mail client bad. This may sound weird but I think opening up Evolution while I still was on Jaunty fixes the problem and it continues to work in Karmic. I'm guessing in Karmic it cannot find the setup wizard screen or something of that nature and crashes. How is everyone doing with Empathy? I notice the one in the Ubuntu repositories have Adium support while the one in the Daily PPA doesn't. Is Adium chatstyle support temporarily disabled? Thanks for the help everyone.

---

### Post by Staz on 2009-07-14
> **Aries K said:**
> Thanks but I fixed the problem by reinstalling Karmic, all is well so far. I needed an E-mail client bad. This may sound weird but I think opening up Evolution while I still was on Jaunty fixes the problem and it continues to work in Karmic. I'm guessing in Karmic it cannot find the setup wizard screen or something of that nature and crashes. How is everyone doing with Empathy? I notice the one in the Ubuntu repositories have Adium support while the one in the Daily PPA doesn't. Is Adium chatstyle support temporarily disabled? Thanks for the help everyone.
I don't know about the daily PPA but for the empathy in trunk the adium support is still here it just doesn't present you a file chooser dialog to select the theme anymore. As someone says you just have to put the theme in $HOME/.local/share/adium/message-styles/ and it will list it with the others themes.

See [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes)

---

### Post by Aries K on 2009-07-15
> **Staz said:**
> I don't know about the daily PPA but for the empathy in trunk the adium support is still here it just doesn't present you a file chooser dialog to select the theme anymore. As someone says you just have to put the theme in $HOME/.local/share/adium/message-styles/ and it will list it with the others themes.

See [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes)

Ah ok that fixed it thanks. Kind of a tricky way to get themes to work. Maybe one day they will have a theme system like Kopete. Oh well on the upside empathy seems to handle themes better (the ones that DO work) than Kopete. I am definitely liking Empathy way more than Pidgin, reminds me of I-chat quite a bit.

---

### Post by Staz on 2009-07-16
> **Aries K said:**
> Ah ok that fixed it thanks. Kind of a tricky way to get themes to work. Maybe one day they will have a theme system like Kopete. Oh well on the upside empathy seems to handle themes better (the ones that DO work) than Kopete. I am definitely liking Empathy way more than Pidgin, reminds me of I-chat quite a bit.
There are plans to make managing themes in empathy a bit more pleasant. For exemple a nicer theme browser and an easier way to install them (probably by supporting adiumxtras:// uri)

Also it was decided to put the themes in this application-neutral directory so Kopete will use it too (I think they have already agreed to do it on the ML) and hopefully any other applications using adium themes

---

### Post by Aries K on 2009-07-16
> **Staz said:**
> There are plans to make managing themes in empathy a bit more pleasant. For exemple a nicer theme browser and an easier way to install them (probably by supporting adiumxtras:// uri)

Also it was decided to put the themes in this application-neutral directory so Kopete will use it too (I think they have already agreed to do it on the ML) and hopefully any other applications using adium themes

Awesome, that sounds good. Empathy is going to be one solid app. :)

---

