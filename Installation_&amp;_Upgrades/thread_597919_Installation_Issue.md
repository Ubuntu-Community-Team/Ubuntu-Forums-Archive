---
title: "Installation Issue"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by num on 2007-10-30
I am trying to install Pidgin 1.5.1 onto Ubuntu version 7.10 (GUTSY) but I am running into issues when i type in "make" in the terminal

here is the issue i get:

[http://pastebin.com/f311ed1b3]("http://pastebin.com/f311ed1b3")


This is the direct link to the file im trying to install: 

[gaim]("http://downloads.sourceforge.net/pidgin/pidgin-1.5.1.tar.gz?modtime=1182441304&big_mirror=1")

what could be the problem and how i fix it? Thanks in advance.

---

### Post by It_Was_Luck on 2007-10-30
In Gusty, Pidgin comes preinstalled... Check your applications list, also its Pidgin 2.2.2 (I believe) which is probably better than 1.5.1

---

### Post by num on 2007-10-30
yes i know its preinstalled but i had it uninstalled and i want to install pidgin 1.5.1 because of personal reasons and cause i perfer it better. anyways can someone please help me install pidgin 1.5.1

---

### Post by num on 2007-10-30
can someone please help me its important

---

### Post by num on 2007-10-31
seriously no one knows why this is happening?

---

### Post by Fire_Chief on 2007-10-31
You could download an RPM for Pidgin and convert it using the alien package (sudo apt-get install alien). This will convert the RPM into a deb file for you to properly install it on the system via the normal tools. I found an RPM for 1.5.1-1 at [http://rpm.pbone.net/index.php3/stat/4/idpl/5245332/com/pidgin-1.5.1-1.el3.i386.rpm.html]("http://rpm.pbone.net/index.php3/stat/4/idpl/5245332/com/pidgin-1.5.1-1.el3.i386.rpm.html")

Cheers,

---

### Post by num on 2007-10-31
im getting tired of this, have you read my first post? im having trouble with the "make" command i have the package tar.gz

---

### Post by num on 2007-10-31
This is the error i get when i try compiling:

> 
pidgin-1.5.1/po/pt_BR.gmo
pidgin-1.5.1/po/sl.gmo
pidgin-1.5.1/po/az.po
pidgin-1.5.1/po/ro.po
pidgin-1.5.1/po/sr@Latn.gmo
pidgin-1.5.1/COPYING
pidgin-1.5.1/compile
pidgin-1.5.1/config.h.in
pidgin-1.5.1/depcomp
pidgin-1.5.1/plugins/
pidgin-1.5.1/plugins/mailchk.c
pidgin-1.5.1/plugins/Makefile.am
pidgin-1.5.1/plugins/idle.c
pidgin-1.5.1/plugins/history.c
pidgin-1.5.1/plugins/simple.c
pidgin-1.5.1/plugins/gestures/
pidgin-1.5.1/plugins/gestures/Makefile.am
pidgin-1.5.1/plugins/gestures/stroke-draw.c
pidgin-1.5.1/plugins/gestures/stroke.c
pidgin-1.5.1/plugins/gestures/gstroke-internal.h
pidgin-1.5.1/plugins/gestures/Makefile.in
pidgin-1.5.1/plugins/gestures/gestures.c
pidgin-1.5.1/plugins/gestures/gstroke.h
pidgin-1.5.1/plugins/ChangeLog.API
pidgin-1.5.1/plugins/timestamp.c
pidgin-1.5.1/plugins/gevolution/
pidgin-1.5.1/plugins/gevolution/Makefile.am
pidgin-1.5.1/plugins/gevolution/eds-utils.c
pidgin-1.5.1/plugins/gevolution/gevolution.c
pidgin-1.5.1/plugins/gevolution/gevo-util.c
pidgin-1.5.1/plugins/gevolution/add_buddy_dialog.c
pidgin-1.5.1/plugins/gevolution/assoc-buddy.c
pidgin-1.5.1/plugins/gevolution/Makefile.in
pidgin-1.5.1/plugins/gevolution/new_person_dialog.c
pidgin-1.5.1/plugins/gevolution/gevolution.h
pidgin-1.5.1/plugins/autorecon.c
pidgin-1.5.1/plugins/raw.c
pidgin-1.5.1/plugins/pluginpref_example.c
pidgin-1.5.1/plugins/HOWTO
pidgin-1.5.1/plugins/notify.c
pidgin-1.5.1/plugins/fortuneprofile.pl
pidgin-1.5.1/plugins/spellchk.c
pidgin-1.5.1/plugins/win32/
pidgin-1.5.1/plugins/win32/winprefs/
pidgin-1.5.1/plugins/win32/winprefs/gtkappbar.c
pidgin-1.5.1/plugins/win32/winprefs/Makefile.mingw
pidgin-1.5.1/plugins/win32/winprefs/winprefs.c
pidgin-1.5.1/plugins/win32/winprefs/gtkappbar.h
pidgin-1.5.1/plugins/win32/transparency/
pidgin-1.5.1/plugins/win32/transparency/Makefile.mingw
pidgin-1.5.1/plugins/win32/transparency/win2ktrans.c
pidgin-1.5.1/plugins/statenotify.c
pidgin-1.5.1/plugins/Makefile.mingw
pidgin-1.5.1/plugins/relnot.c
pidgin-1.5.1/plugins/docklet/
pidgin-1.5.1/plugins/docklet/Makefile.am
pidgin-1.5.1/plugins/docklet/docklet.c
pidgin-1.5.1/plugins/docklet/eggtrayicon.h
pidgin-1.5.1/plugins/docklet/Makefile.mingw
pidgin-1.5.1/plugins/docklet/docklet.h
pidgin-1.5.1/plugins/docklet/docklet-x11.c
pidgin-1.5.1/plugins/docklet/Makefile.in
pidgin-1.5.1/plugins/docklet/eggtrayicon.c
pidgin-1.5.1/plugins/docklet/docklet-win32.c
pidgin-1.5.1/plugins/extplacement.c
pidgin-1.5.1/plugins/purple-remote/
pidgin-1.5.1/plugins/purple-remote/Makefile.am
pidgin-1.5.1/plugins/purple-remote/remote.h
pidgin-1.5.1/plugins/purple-remote/remote-socket.h
pidgin-1.5.1/plugins/purple-remote/remote.c
pidgin-1.5.1/plugins/purple-remote/remote-socket.c
pidgin-1.5.1/plugins/purple-remote/Makefile.in
pidgin-1.5.1/plugins/Makefile.in
pidgin-1.5.1/plugins/gaim.pl
pidgin-1.5.1/plugins/tcl/
pidgin-1.5.1/plugins/tcl/Makefile.am
pidgin-1.5.1/plugins/tcl/tcl_cmds.c
pidgin-1.5.1/plugins/tcl/tcl_win32.c
pidgin-1.5.1/plugins/tcl/tcl_glib.c
pidgin-1.5.1/plugins/tcl/Makefile.mingw
pidgin-1.5.1/plugins/tcl/tcl_glib.h
pidgin-1.5.1/plugins/tcl/tcl_gaim.h
pidgin-1.5.1/plugins/tcl/tcl.c
pidgin-1.5.1/plugins/tcl/signal-test.tcl
pidgin-1.5.1/plugins/tcl/Makefile.in
pidgin-1.5.1/plugins/tcl/tcl_signals.c
pidgin-1.5.1/plugins/tcl/TCL-HOWTO
pidgin-1.5.1/plugins/ChangeLog
pidgin-1.5.1/plugins/perl/
pidgin-1.5.1/plugins/perl/Makefile.am
pidgin-1.5.1/plugins/perl/perl-handlers.h
pidgin-1.5.1/plugins/perl/common/
pidgin-1.5.1/plugins/perl/common/ConvWindow.xs
pidgin-1.5.1/plugins/perl/common/Gaim.pm
pidgin-1.5.1/plugins/perl/common/typemap
pidgin-1.5.1/plugins/perl/common/Conversation_IM.xs
pidgin-1.5.1/plugins/perl/common/BuddyList_Group.xs
pidgin-1.5.1/plugins/perl/common/module.h
pidgin-1.5.1/plugins/perl/common/Makefile.mingw
pidgin-1.5.1/plugins/perl/common/BuddyList_Buddy.xs
pidgin-1.5.1/plugins/perl/common/Conversation_Chat.xs
pidgin-1.5.1/plugins/perl/common/Account.xs
pidgin-1.5.1/plugins/perl/common/Connection.xs
pidgin-1.5.1/plugins/perl/common/Gaim.xs
pidgin-1.5.1/plugins/perl/common/Makefile.PL.in
pidgin-1.5.1/plugins/perl/common/fallback/
pidgin-1.5.1/plugins/perl/common/fallback/const-xs.inc
pidgin-1.5.1/plugins/perl/common/fallback/const-c.inc
pidgin-1.5.1/plugins/perl/common/Conversation.xs
pidgin-1.5.1/plugins/perl/common/BuddyList_Chat.xs
pidgin-1.5.1/plugins/perl/common/BuddyList.xs
pidgin-1.5.1/plugins/perl/perl-handlers.c
pidgin-1.5.1/plugins/perl/Makefile.mingw
pidgin-1.5.1/plugins/perl/Makefile.in
pidgin-1.5.1/plugins/perl/perl-common.c
pidgin-1.5.1/plugins/perl/perl-common.h
pidgin-1.5.1/plugins/perl/perl.c
pidgin-1.5.1/plugins/filectl.c
pidgin-1.5.1/plugins/signals-test.c
pidgin-1.5.1/plugins/ticker/
pidgin-1.5.1/plugins/ticker/Makefile.am
pidgin-1.5.1/plugins/ticker/ticker.c
pidgin-1.5.1/plugins/ticker/Makefile.mingw
pidgin-1.5.1/plugins/ticker/gtkticker.c
pidgin-1.5.1/plugins/ticker/Makefile.in
pidgin-1.5.1/plugins/ticker/gtkticker.h
pidgin-1.5.1/plugins/ssl/
pidgin-1.5.1/plugins/ssl/Makefile.am
pidgin-1.5.1/plugins/ssl/ssl-gnutls.c
pidgin-1.5.1/plugins/ssl/Makefile.mingw
pidgin-1.5.1/plugins/ssl/ssl.c
pidgin-1.5.1/plugins/ssl/Makefile.in
pidgin-1.5.1/plugins/ssl/ssl-nss.c
pidgin-1.5.1/plugins/iconaway.c
pidgin-1.5.1/Makefile.mingw
pidgin-1.5.1/AUTHORS
pidgin-1.5.1/INSTALL
pidgin-1.5.1/pixmaps/
pidgin-1.5.1/pixmaps/Makefile.am
pidgin-1.5.1/pixmaps/gaim_msgunread_4bit_16.ico
pidgin-1.5.1/pixmaps/insert-link-small.png
pidgin-1.5.1/pixmaps/about_menu.png
pidgin-1.5.1/pixmaps/edit.png
pidgin-1.5.1/pixmaps/gaim_16.ico
pidgin-1.5.1/pixmaps/away.png
pidgin-1.5.1/pixmaps/pause.png
pidgin-1.5.1/pixmaps/tb_drag_arrow_left.xpm
pidgin-1.5.1/pixmaps/tb_drag_arrow_up.xpm
pidgin-1.5.1/pixmaps/gaim_away_4bit_16.ico
pidgin-1.5.1/pixmaps/gaim_blank_4bit_16.ico
pidgin-1.5.1/pixmaps/typing.png
pidgin-1.5.1/pixmaps/change-fgcolor-small.png
pidgin-1.5.1/pixmaps/gaim.png
pidgin-1.5.1/pixmaps/tb_drag_arrow_right.xpm
pidgin-1.5.1/pixmaps/change-bgcolor-small.png
pidgin-1.5.1/pixmaps/gaim_away.ico
pidgin-1.5.1/pixmaps/smileys/
pidgin-1.5.1/pixmaps/smileys/Makefile.am
pidgin-1.5.1/pixmaps/smileys/Makefile.mingw
pidgin-1.5.1/pixmaps/smileys/none/
pidgin-1.5.1/pixmaps/smileys/none/Makefile.am
pidgin-1.5.1/pixmaps/smileys/none/theme
pidgin-1.5.1/pixmaps/smileys/none/Makefile.mingw
pidgin-1.5.1/pixmaps/smileys/none/Makefile.in
pidgin-1.5.1/pixmaps/smileys/default/
pidgin-1.5.1/pixmaps/smileys/default/Makefile.am
pidgin-1.5.1/pixmaps/smileys/default/msn_sleepy.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_turtle.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_wink.gif
pidgin-1.5.1/pixmaps/smileys/default/theme
pidgin-1.5.1/pixmaps/smileys/default/msn_car.png
pidgin-1.5.1/pixmaps/smileys/default/msn_brb.png
pidgin-1.5.1/pixmaps/smileys/default/msn_clock.png
pidgin-1.5.1/pixmaps/smileys/default/msn_cat.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_cow.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_laughloud.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_thumbup.png
pidgin-1.5.1/pixmaps/smileys/default/msn_note.png
pidgin-1.5.1/pixmaps/smileys/default/wink.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_ooooh.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_neutral.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_malefighter1.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_sick.png
pidgin-1.5.1/pixmaps/smileys/default/msn_photo.png
pidgin-1.5.1/pixmaps/smileys/default/msn_email.png
pidgin-1.5.1/pixmaps/smileys/default/msn_island.png
pidgin-1.5.1/pixmaps/smileys/default/msn_plane.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_shame.gif
pidgin-1.5.1/pixmaps/smileys/default/download.png
pidgin-1.5.1/pixmaps/smileys/default/msn_ooooh.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_rotfl.gif
pidgin-1.5.1/pixmaps/smileys/default/mrt.png
pidgin-1.5.1/pixmaps/smileys/default/msn_teeth.png
pidgin-1.5.1/pixmaps/smileys/default/msn_cake.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_talktohand.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_plate.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_love.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_nerd.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_alien2.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_neutral.png
pidgin-1.5.1/pixmaps/smileys/default/bigsmile.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_worship.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_alien.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_donttell.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_liar.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_cigarette.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_eyebrow.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_idea.png
pidgin-1.5.1/pixmaps/smileys/default/farted.png
pidgin-1.5.1/pixmaps/smileys/default/oneeye.png
pidgin-1.5.1/pixmaps/smileys/default/msn_sleep.png
pidgin-1.5.1/pixmaps/smileys/default/msn_sad.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_youkiddingme.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_flag.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_sun.png
pidgin-1.5.1/pixmaps/smileys/default/msn_weird.png
pidgin-1.5.1/pixmaps/smileys/default/msn_devil.png
pidgin-1.5.1/pixmaps/smileys/default/yell.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_drool.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_angry.png
pidgin-1.5.1/pixmaps/smileys/default/cry.png
pidgin-1.5.1/pixmaps/smileys/default/msn_heart.png
pidgin-1.5.1/pixmaps/smileys/default/msn_boy.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_party.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_kiss.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_madtongue.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_angry.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_tongue.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_tongue.png
pidgin-1.5.1/pixmaps/smileys/default/msn_coins.png
pidgin-1.5.1/pixmaps/smileys/default/msn_icon.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_huggs.gif
pidgin-1.5.1/pixmaps/smileys/default/embarrassed.png
pidgin-1.5.1/pixmaps/smileys/default/think.png
pidgin-1.5.1/pixmaps/smileys/default/crazy.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_coffee.gif
pidgin-1.5.1/pixmaps/smileys/default/crossedlips.png
pidgin-1.5.1/pixmaps/smileys/default/angel.png
pidgin-1.5.1/pixmaps/smileys/default/burp.png
pidgin-1.5.1/pixmaps/smileys/default/msn_sheep.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_monkey.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_run.png
pidgin-1.5.1/pixmaps/smileys/default/Makefile.mingw
pidgin-1.5.1/pixmaps/smileys/default/yahoo_sunglas.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_sad.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_chicken.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_smiley.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_mean.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_girl.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_silly.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_cellphone.png
pidgin-1.5.1/pixmaps/smileys/default/msn_dontknow.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_doh.gif
pidgin-1.5.1/pixmaps/smileys/default/kiss.png
pidgin-1.5.1/pixmaps/smileys/default/msn_wink.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_bigsmile.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_malefighter2.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_pray.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_umbrella.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_waiting.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_sick.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_film.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_brokenheart.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_bat.gif
pidgin-1.5.1/pixmaps/smileys/default/sad.png
pidgin-1.5.1/pixmaps/smileys/default/msn_embarrassed.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_whistling.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_flower.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_tired.gif
pidgin-1.5.1/pixmaps/smileys/default/cool.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_dance.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_beatup.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_think.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_soccer.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_peace.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_clown.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_occ.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_question.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_coffee.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_idea.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_bowl.png
pidgin-1.5.1/pixmaps/smileys/default/msn_deadflower.png
pidgin-1.5.1/pixmaps/smileys/default/msn_thumbdown.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_clap.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_secret.png
pidgin-1.5.1/pixmaps/smileys/default/msn_lightning.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_devil.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_sighing.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_worried.gif
pidgin-1.5.1/pixmaps/smileys/default/smile.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_femalefighter.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_sarcastic.png
pidgin-1.5.1/pixmaps/smileys/default/msn_fingerscrossed.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_bye.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_pizza.png
pidgin-1.5.1/pixmaps/smileys/default/msn_computer.png
pidgin-1.5.1/pixmaps/smileys/default/msn_laugh.png
pidgin-1.5.1/pixmaps/smileys/default/Makefile.in
pidgin-1.5.1/pixmaps/smileys/default/msn_rainbow.png
pidgin-1.5.1/pixmaps/smileys/default/msn_question.png
pidgin-1.5.1/pixmaps/smileys/default/msn_drink.png
pidgin-1.5.1/pixmaps/smileys/default/msn_star.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_giggle.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_sleep.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_cry.gif
pidgin-1.5.1/pixmaps/smileys/default/scream.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_blush.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_moneyeyes.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_eyeroll.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_stormy.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_pumpkin.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_eyeroll.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_xbox.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_glasses.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_hypnotized.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_shhhh.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_smiley.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_frustrated.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_beer.png
pidgin-1.5.1/pixmaps/smileys/default/msn_runback.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_waving.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_ghost.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_think.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_away.png
pidgin-1.5.1/pixmaps/smileys/default/msn_angel.png
pidgin-1.5.1/pixmaps/smileys/default/msn_sunglasses.png
pidgin-1.5.1/pixmaps/smileys/default/msn_dog.png
pidgin-1.5.1/pixmaps/smileys/default/msn_hot.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_yingyang.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_handcuffs.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_shamrock.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_flower.png
pidgin-1.5.1/pixmaps/smileys/default/moneymouth.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_pig.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_cry.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_sweating.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_snail.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_batting.gif
pidgin-1.5.1/pixmaps/smileys/default/luke.png
pidgin-1.5.1/pixmaps/smileys/default/msn_phone.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_star.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_brheart.png
pidgin-1.5.1/pixmaps/smileys/default/tongue.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_nailbiting.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_loser.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_highfive.png
pidgin-1.5.1/pixmaps/smileys/default/msn_gift.png
pidgin-1.5.1/pixmaps/smileys/default/yahoo_angel.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_silent.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_cowboy.gif
pidgin-1.5.1/pixmaps/smileys/default/msn_online.png
pidgin-1.5.1/pixmaps/smileys/default/msn_party.gif
pidgin-1.5.1/pixmaps/smileys/default/yahoo_kiss.gif
pidgin-1.5.1/pixmaps/smileys/Makefile.in
pidgin-1.5.1/pixmaps/gaim_offline.ico
pidgin-1.5.1/pixmaps/text_bigger.png
pidgin-1.5.1/pixmaps/send-im.png
pidgin-1.5.1/pixmaps/Makefile.mingw
pidgin-1.5.1/pixmaps/logo.png
pidgin-1.5.1/pixmaps/status/
pidgin-1.5.1/pixmaps/status/Makefile.am
pidgin-1.5.1/pixmaps/status/Makefile.mingw
pidgin-1.5.1/pixmaps/status/default/
pidgin-1.5.1/pixmaps/status/default/Makefile.am
pidgin-1.5.1/pixmaps/status/default/zephyr.png
pidgin-1.5.1/pixmaps/status/default/novell.png
pidgin-1.5.1/pixmaps/status/default/invisible.png
pidgin-1.5.1/pixmaps/status/default/nr.png
pidgin-1.5.1/pixmaps/status/default/away.png
pidgin-1.5.1/pixmaps/status/default/extendedaway.png
pidgin-1.5.1/pixmaps/status/default/silc.png
pidgin-1.5.1/pixmaps/status/default/napster.png
pidgin-1.5.1/pixmaps/status/default/na.png
pidgin-1.5.1/pixmaps/status/default/occupied.png
pidgin-1.5.1/pixmaps/status/default/halfop.png
pidgin-1.5.1/pixmaps/status/default/notauthorized.png
pidgin-1.5.1/pixmaps/status/default/logout.png
pidgin-1.5.1/pixmaps/status/default/op.png
pidgin-1.5.1/pixmaps/status/default/Makefile.mingw
pidgin-1.5.1/pixmaps/status/default/voice.png
pidgin-1.5.1/pixmaps/status/default/jabber.png
pidgin-1.5.1/pixmaps/status/default/game.png
pidgin-1.5.1/pixmaps/status/default/login.png
pidgin-1.5.1/pixmaps/status/default/offline.png
pidgin-1.5.1/pixmaps/status/default/admin.png
pidgin-1.5.1/pixmaps/status/default/msn.png
pidgin-1.5.1/pixmaps/status/default/freeforchat.png
pidgin-1.5.1/pixmaps/status/default/aim.png
pidgin-1.5.1/pixmaps/status/default/secure.png
pidgin-1.5.1/pixmaps/status/default/ignored.png
pidgin-1.5.1/pixmaps/status/default/founder.png
pidgin-1.5.1/pixmaps/status/default/female.png
pidgin-1.5.1/pixmaps/status/default/hiptop.png
pidgin-1.5.1/pixmaps/status/default/Makefile.in
pidgin-1.5.1/pixmaps/status/default/gadu-gadu.png
pidgin-1.5.1/pixmaps/status/default/yahoo.png
pidgin-1.5.1/pixmaps/status/default/activebuddy.png
pidgin-1.5.1/pixmaps/status/default/trepia.png
pidgin-1.5.1/pixmaps/status/default/male.png
pidgin-1.5.1/pixmaps/status/default/dnd.png
pidgin-1.5.1/pixmaps/status/default/icq.png
pidgin-1.5.1/pixmaps/status/default/bonjour.png
pidgin-1.5.1/pixmaps/status/default/aol.png
pidgin-1.5.1/pixmaps/status/default/blocked.png
pidgin-1.5.1/pixmaps/status/default/wireless.png
pidgin-1.5.1/pixmaps/status/default/irc.png
pidgin-1.5.1/pixmaps/status/Makefile.in
pidgin-1.5.1/pixmaps/offline.png
pidgin-1.5.1/pixmaps/msgpend.png
pidgin-1.5.1/pixmaps/text_normal.png
pidgin-1.5.1/pixmaps/gaim-install.ico
pidgin-1.5.1/pixmaps/insert-image-small.png
pidgin-1.5.1/pixmaps/accounts.png
pidgin-1.5.1/pixmaps/msgunread.png
pidgin-1.5.1/pixmaps/tb_drag_arrow_down.xpm
pidgin-1.5.1/pixmaps/gaim_msgunread_16.ico
pidgin-1.5.1/pixmaps/info.png
pidgin-1.5.1/pixmaps/gaim_offline_16.ico
pidgin-1.5.1/pixmaps/text_smaller.png
pidgin-1.5.1/pixmaps/gaim_cool.png
pidgin-1.5.1/pixmaps/gaim_auth.png
pidgin-1.5.1/pixmaps/gaim_info.png
pidgin-1.5.1/pixmaps/Makefile.in
pidgin-1.5.1/pixmaps/gaim_warning.png
pidgin-1.5.1/pixmaps/insert-smiley-small.png
pidgin-1.5.1/pixmaps/gaim_error.png
pidgin-1.5.1/pixmaps/gaim_question.png
pidgin-1.5.1/pixmaps/gaim_msgpend_4bit_16.ico
pidgin-1.5.1/pixmaps/typed.png
pidgin-1.5.1/pixmaps/online.png
pidgin-1.5.1/pixmaps/gaim_4bit_16.ico
pidgin-1.5.1/pixmaps/connect.png
pidgin-1.5.1/pixmaps/gaim_msgpend_16.ico
pidgin-1.5.1/pixmaps/gaim_away_16.ico
pidgin-1.5.1/pixmaps/gaim.ico
pidgin-1.5.1/pixmaps/gaim_offline_4bit_16.ico
pidgin-1.5.1/setup-gettext
pidgin-1.5.1/acinclude.m4
pidgin-1.5.1/pidgin.spec
pidgin-1.5.1/purple2blt.pl
pidgin-1.5.1/configure.ac
pidgin-1.5.1/Doxyfile.in
pidgin-1.5.1/config.h
pidgin-1.5.1/ltmain.sh
pidgin-1.5.1/ABOUT-NLS
pidgin-1.5.1/README.mingw
pidgin-1.5.1/config.h.mingw
pidgin-1.5.1/Makefile.in
pidgin-1.5.1/sounds/
pidgin-1.5.1/sounds/arrive.wav
pidgin-1.5.1/sounds/Makefile.am
pidgin-1.5.1/sounds/send.wav
pidgin-1.5.1/sounds/redalert.wav
pidgin-1.5.1/sounds/leave.wav
pidgin-1.5.1/sounds/Makefile.in
pidgin-1.5.1/sounds/receive.wav
pidgin-1.5.1/ChangeLog
pidgin-1.5.1/VERSION.in
pidgin-1.5.1/pidgin.apspec.in
pidgin-1.5.1/COPYRIGHT
pidgin-1.5.1/doc/
pidgin-1.5.1/doc/Makefile.am
pidgin-1.5.1/doc/pidgins_funniest_home_convos.txt
pidgin-1.5.1/doc/gtkblist-signals.dox
pidgin-1.5.1/doc/plugin-ids.dox
pidgin-1.5.1/doc/pidgin.1.in
pidgin-1.5.1/doc/the_penguin.txt
pidgin-1.5.1/doc/gtkimhtml-signals.dox
pidgin-1.5.1/doc/connection-signals.dox
pidgin-1.5.1/doc/FAQ
pidgin-1.5.1/doc/Makefile.in
pidgin-1.5.1/doc/conversation-signals.dox
pidgin-1.5.1/doc/account-signals.dox
pidgin-1.5.1/doc/gtkaccount-signals.dox
pidgin-1.5.1/doc/gtkconv-signals.dox
pidgin-1.5.1/doc/PERL-HOWTO.dox
pidgin-1.5.1/doc/blist-signals.dox
pidgin-1.5.1/doc/CREDITS
pidgin-1.5.1/doc/purple-remote.1.in
pidgin-1.5.1/NEWS
pidgin-1.5.1/pidgin.spec.in
pidgin-1.5.1/config.guess
administrator@server:~/Desktop$ cd pidgin-1.5.1
administrator@server:~/Desktop/pidgin-1.5.1$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
administrator@server:~/Desktop/pidgin-1.5.1$ make
make: *** No targets specified and no makefile found.  Stop.
administrator@server:~/Desktop/pidgin-1.5.1$ 



---

### Post by meindian523 on 2007-10-31
Try installing after installing the build tools

```
sudo apt-get install build-essential
```

---

