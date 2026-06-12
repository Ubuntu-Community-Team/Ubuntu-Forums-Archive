---
title: "Yay another error! Brasero related."
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by JudasReanimated on 2007-08-05
Trying to install Brasero CD/DVD Burning Software, and I'm getting this message.

[B]Requested 'gtk+-2.0 >= 2.10.0' but version of GTK+ is 2.8.20
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'libnautilus-burn' found
No package 'gstreamer-0.10' found
No package 'gstreamer-plugins-base-0.10' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BRASERO_CFLAGS
and BRASERO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
[/B]

Please help me, it seems that every program I want bad errors, and before you mention it, no it's not in Synaptic. 

Thanks for your help and also please someone assist with my QDVD Authoring Problem.

---

### Post by JudasReanimated on 2007-08-06
Is anybody there?

---

### Post by kelvin spratt on 2007-08-06
[http://www.getdeb.net/](http://www.getdeb.net/) has the deb Make sure your repositories are enabled i thought it was in there. but get deb is the latest

---

### Post by JudasReanimated on 2007-08-06
OMFG I am forever in your debt, marry me, use me, abuse me! 

You just made my day!!!!!

---

### Post by Pygi on 2007-08-06
> **JudasReanimated said:**
> Trying to install Brasero CD/DVD Burning Software, and I'm getting this message.

[B]Requested 'gtk+-2.0 >= 2.10.0' but version of GTK+ is 2.8.20
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'libnautilus-burn' found
No package 'gstreamer-0.10' found
No package 'gstreamer-plugins-base-0.10' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BRASERO_CFLAGS
and BRASERO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
[/B]

Please help me, it seems that every program I want bad errors, and before you mention it, no it's not in Synaptic. 

Thanks for your help and also please someone assist with my QDVD Authoring Problem.

1)You need development packages (-dev) for all of those when compiling Brasero manually
2)Brasero can be found in the Universe component of Ubuntu repositories, therefore if you
have it enabled, it does appear in Synaptic

[QUOTE=JudasReanimated]
Is anybody there?
[/QUOTE]

People volunteer to help on the forums. Please be patient, and wait for an
answer.

KR,
M.

---

### Post by Pygi on 2007-08-06
> **kelvin spratt said:**
> [http://www.getdeb.net/](http://www.getdeb.net/) has the deb Make sure your repositories are enabled i thought it was in there. but get deb is the latest

Suggesting 3rd party repositories is not a solution. It often contains broken packages, makes upgrades from official repositories hard, and can sometime even completely break system. Ubuntu Gutsy includes Brasero 0.6.0 (newest upstream) with several patches applied, and is recommended for usage.

Thank you,
M.

---

### Post by JudasReanimated on 2007-08-06
Sorry dude, I hate to be rude man, but you're wrong. It's not in my synaptic, and I have all repositories enabled. Also be patient. I had two questions on here for over a week without responses, I was just getting a little annoyed. Finally I have all the .dev of the packages you mentioned, still have the issue. Dunno why, that was why I came here, no reason to act condesending towards me, and complain about the only real help I actually received.

Didn't mean for that to sound nasty, but still it's kinda annoying.

---

### Post by Pygi on 2007-08-07
> **JudasReanimated said:**
> Sorry dude, I hate to be rude man, but you're wrong. It's not in my synaptic, and I have all repositories enabled. Also be patient. I had two questions on here for over a week without responses, I was just getting a little annoyed. Finally I have all the .dev of the packages you mentioned, still have the issue. Dunno why, that was why I came here, no reason to act condesending towards me, and complain about the only real help I actually received.

Didn't mean for that to sound nasty, but still it's kinda annoying.

I am not wrong. You however might be using a release where Brasero wasn't in repositories.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=brasero&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=brasero&searchon=names&subword=1&version=all&release=all)

First of all, read what the ./configure says when you are trying to compile brasero. The first thing it complains about is outdated gtk. If repositories of the release you use have newer, just upgrade - 
you'll also need the dev package, libgtk2.0-dev. Then move on to the next error, and so on.

M.

---

### Post by JudasReanimated on 2007-08-08
You keep not understanding. I have all the packages it's asking for installed. My Repositories are fully upgraded, and I'm also using the sources.list that one of the staff members reccomended. Also I have uncomented all my repositories. I don't know any other way to explain to you that what you're telling me isn't going to work, hasn't work, and can't work for me. I mean if you'd like I could remove and reinstall everything you tell me to install, but I seriously doubt they're installed wrong anyway. 

Also try not to be so overzealous, and acting as if everything you say is correct, even though foir my problem it's not working in the slightest. I'm assuming that the path variable is off somehow, but I'm not sure how to check it. I've had a problem before where dapper wouldn't even compile anything even after I got the build-essentials. 

That required a complete format and reinstall to get that working.

*Edit* Here as you can see my Synaptic with all repos enabled only shows the current Brasero I have installed from GetDeb.
[http://img265.imageshack.us/my.php?image=screenshotzo2.png](http://img265.imageshack.us/my.php?image=screenshotzo2.png)

That means no other version is in Synaptic, unless it's under Bonfire, which I couldn't find either.

---

### Post by Pygi on 2007-08-09
> **JudasReanimated said:**
> You keep not understanding. I have all the packages it's asking for installed. My Repositories are fully upgraded, and I'm also using the sources.list that one of the staff members reccomended. Also I have uncomented all my repositories. I don't know any other way to explain to you that what you're telling me isn't going to work, hasn't work, and can't work for me. I mean if you'd like I could remove and reinstall everything you tell me to install, but I seriously doubt they're installed wrong anyway. 

Also try not to be so overzealous, and acting as if everything you say is correct, even though foir my problem it's not working in the slightest. I'm assuming that the path variable is off somehow, but I'm not sure how to check it. I've had a problem before where dapper wouldn't even compile anything even after I got the build-essentials. 

That required a complete format and reinstall to get that working.

*Edit* Here as you can see my Synaptic with all repos enabled only shows the current Brasero I have installed from GetDeb.
[http://img265.imageshack.us/my.php?image=screenshotzo2.png](http://img265.imageshack.us/my.php?image=screenshotzo2.png)

That means no other version is in Synaptic, unless it's under Bonfire, which I couldn't find either.

You keep insisting on not listening to me :) 
Anyway, if you have dapper (which you didn't say) Brasero indeed wasn't in repositories
back then, and I've told you that a couple of posts above. Also, Brasero 0.4.4 you installed from
getdeb is hardly newest, since Ubuntu Gutsy has 0.6.0 :)

KR,
M.

---

### Post by Pygi on 2007-08-09
> **JudasReanimated said:**
> You keep not understanding. I have all the packages it's asking for installed. .

No, you don't. Especially if you have Dapper :)

Requested 'gtk+-2.0 >= 2.10.0' but version of GTK+ is 2.8.20

Since Dapper didn't have 2.10.x ..... 
well you get my point ;)

KR,
M.

---

### Post by JudasReanimated on 2007-08-09
Look at my name, then move your eyes slightly to the right, and you'll see exactly which Ubuntu I'm using, also I kinda figured out that brasero 6.0 wasn't going to work, though maybe I'm wrong on that. 

I understood what you were saying, and what I was trying to tell you is that I had everything it asked for, except possibly GTK 2.10, as I have 2.8, but still Brasero 4.4 works like a charm, and for some reason you can't seem to get that I'm saying you aren't helping, and you're just being an condescending *** about everything.

What caught my eye and why I cam here, was mostly because I knew damn well that I had the exact version of GStreamer it asked for and the .dev as I had just installed them prior for another app. Of course though in your all knowing logic you knew that my eyes were lying to me, and that not only did I not have that, but I also must be an idiot, because the repos had my brasero, of course that was until I posted a pic proving you were full of it on that one.

Also don't give me the "I didn't know your Ubuntu version", that was total BS, it's displayed to everyone clearly, 

Now of course you'll simply explain that you unlike everyone else didn't pay any attention to that as you assumed I was using 7.04, but of course nothing really matters on here as the problem is solved for now.

Thanks for your time,
                                James

---

### Post by Pygi on 2007-08-09
Hello,

do what you wish, I'm glad it's working for you. I hope that when you upgrade
you'll find Brasero working even better.

KR,
M.
-------
Brasero packager for Ubuntu ;)

---

### Post by Pygi on 2007-08-09
> **JudasReanimated said:**
> L and that not only did I not have that, but I also must be an idiot, because the repos had my brasero, of course that was until I posted a pic proving you were full of it on that one.


I don't think you are a idiot, so false statement :)
Anyway, enough of it :)

Have fun, 
M.

---

### Post by JudasReanimated on 2007-08-10
Just how you came off, but yeah this is old, and I intend on upgrading when I get a new PC. Current one is a PoS.

---

