---
title: "Installing libflashplayer.so"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by tgckpg on 2011-01-26
Hi, I'm newbie of linux.(Caught me in 5 mins to become a linux fans)

I tried to install flashplayer debugger ver for chrome.
I searched google for 2 days and couldn't found a solution.

The most common I got is to make the plugins into whatever "libflashplayer original" in(Including making a even-non-exist directory to chrome folder) and I replace them all with the new one.

Then using google-chrome --enable-plugins.
And type about:plugins at the address bar.

I got nothing about flashplayer!!



Ubuntu desktop 10.10 amd64. Chrome 10.0.642.2 dev

Please help me to fix it.

Many thanks.


--------Oh, and I got these output when running chrome~~~~~
```

[32045:32045:14318302937:ERROR:native_library_linux.cc(32)] dlopen failed when trying to open default_plugin: default_plugin: cannot open shared object file: No such file or directory
[31945:32042:14319665031:ERROR:x509_certificate_nss.cc(567)] No EV Policy Tag

```

Currently using flashplugin64-installer package(Not debugger!!) for chrome.

---

### Post by gordintoronto on 2011-01-26
What you should have done is use Synaptic Package Manager to install the "restricted extras". I'm not sure how you can *first* get rid of the inappropriate stuff you have installed.

---

### Post by steveneddy on 2011-01-26
Open a terminal and type this in:

```
sudo apt-get install flashplugin-nonfree
```

enter your password when prompted

away you go.

Of course, restart your browser then check it with YouTube or something.

---

### Post by tgckpg on 2011-01-27
OK. I'm reeeally NEW of linux. What is restricted extras?
I'm sorry. Itseems not a debgger ver of flash player.

---

### Post by jocko on 2011-01-27
If you're using 64 bit ubuntu, it's better to install the 64 bit flash plugin. The easiest way is to install the firefox addon [flash-aid]("https://addons.mozilla.org/sv-se/firefox/addon/flash-aid/") and let it install the proper flash plugin for you.

---

### Post by tgckpg on 2011-01-27
Please, I need debugger ver.

---

### Post by Todd in Berlin on 2011-04-15
> **jocko said:**
> If you're using 64 bit ubuntu, it's better to install the 64 bit flash plugin. The easiest way is to install the firefox addon [flash-aid]("https://addons.mozilla.org/sv-se/firefox/addon/flash-aid/") and let it install the proper flash plugin for you.

I DOWNLOADED this and extracted it but cannot figure out how to install it or let install Flash... BUT also will it install the latest Beta version of Flash for 64-bit?

Using the above instructions via Terminal I re-installed Flash, but it seems to not function properly in Opera (e.g. I can see You Tube videos but on the Aljazeera English channel I can watch saved video but not the Live Stream.)

And with Chrome in You Tube I just get the message "An error occurred. Please try again later."


The Aljazeera Livestream worked before I had a problem with an overzealous Computer Janitor which removed Opera. I re-stalled it and it had the new Flash problem.

Thanks!

---

### Post by jocko on 2011-04-17
> **Todd in Berlin said:**
> I DOWNLOADED this and extracted it but cannot figure out how to install it or let install Flash... BUT also will it install the latest Beta version of Flash for 64-bit?
Why would you download it? It's a firefox plugin. Just click the "add to firefox" button on the page I linked to and it will be installed.
To make it install the flash plugin, just open up firefox and click tools-->additions and click the "settings" button on the flashaid plugin. The rest should be obvious. The default is to install the 64 bit plugin (but this can be changed if you enable "expert mode").

---

### Post by thenickrulz on 2011-04-17
> **jocko said:**
> Why would you download it? It's a firefox plugin. Just click the "add to firefox" button on the page I linked to and it will be installed.
To make it install the flash plugin, just open up firefox and click tools-->additions and click the "settings" button on the flashaid plugin. The rest should be obvious. The default is to install the 64 bit plugin (but this can be changed if you enable "expert mode").
Flash aid is great.. i have it on firefox 4 and it works a treat!:p

---

