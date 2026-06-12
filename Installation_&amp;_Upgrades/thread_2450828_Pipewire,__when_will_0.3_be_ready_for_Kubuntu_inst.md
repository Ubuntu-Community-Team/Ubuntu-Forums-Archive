---
title: "Pipewire,  when will 0.3 be ready for Kubuntu install?"
date: 2020-09-21
forum: Installation &amp; Upgrades
---

### Post by Dirk_Ouellette on 2020-09-21
When will I be able to have pipewire instead of jack, etc. on my kubuntu/KXstudio machine.

---

### Post by Dirk_Ouellette on 2020-10-27
[FONT=monospace][COLOR=#000000][/COLOR][COLOR=#5454ff][B]I am well and truly over my head here.   Can someone help me move forward?
Thank you

~[/B][/COLOR][COLOR=#000000]$ git clone [https://gitlab.freedesktop.org/pipewire/pipewire.gi](https://gitlab.freedesktop.org/pipewire/pipewire.gi)[/COLOR]
t 
Cloning into 'pipewire'... 
remote: Enumerating objects: 701, done. 
remote: Counting objects: 100% (701/701), done. 
remote: Compressing objects: 100% (320/320), done. 
remote: Total 51074 (delta 487), reused 558 (delta 381), pack-reused 50373 
Receiving objects: 100% (51074/51074), 26.78 MiB | 1.80 MiB/s, done. 
Resolving deltas: 100% (40504/40504), done. 
[COLOR=#5454ff][B]
~[/B][/COLOR][COLOR=#000000]$ ./autogen.sh --prefix=$PREFIX [/COLOR]
bash: ./autogen.sh: No such file or directory 
[COLOR=#54ff54]****[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls [/COLOR]
[COLOR=#5454ff]**Desktop**[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#5454ff]**Downloads**[/COLOR][COLOR=#000000]                      [/COLOR][COLOR=#5454ff]**Music**[/COLOR][COLOR=#000000]     [/COLOR][COLOR=#5454ff]**pipewire**[/COLOR][COLOR=#000000]  [/COLOR][COLOR=#5454ff]**Templates**[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#5454ff]**Documents**[/COLOR][COLOR=#000000]  [/COLOR][COLOR=#ff5454]**kxstudio-repos_10.0.3_all.deb**[/COLOR][COLOR=#000000]  [/COLOR][COLOR=#5454ff]**Pictures**[/COLOR][COLOR=#000000]  [/COLOR][COLOR=#5454ff]**Public**[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#5454ff]**Videos**[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#000000][/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cd pipewire [/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#5454ff]**~/pipewire**[/COLOR][COLOR=#000000]$ ./autogen.sh --prefix=$PREFIX [/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#5454ff]**~/pipewire**[/COLOR][COLOR=#000000]$ make [/COLOR]
make: *** No targets specified and no makefile found.  Stop. 
[COLOR=#000000]
[/COLOR][COLOR=#5454ff]**~/pipewire**[/COLOR][COLOR=#000000]$ ls [/COLOR]
[COLOR=#54ff54]**autogen.sh**[/COLOR][COLOR=#000000]                [/COLOR][COLOR=#5454ff]**doc**[/COLOR][COLOR=#000000]          meson_options.txt    PROTOCOL [/COLOR]
[COLOR=#54ff54]**check_missing_headers.sh**[/COLOR][COLOR=#000000]  INSTALL.md   NEWS                 [/COLOR][COLOR=#54ff54]**pw-uninstalled.sh**[/COLOR][COLOR=#000000] [/COLOR]
CODE_OF_CONDUCT.md        LICENSE      [COLOR=#5454ff]**pipewire-alsa**[/COLOR][COLOR=#000000]        README.md [/COLOR]
config.h.meson            Makefile.in  [COLOR=#5454ff]**pipewire-jack**[/COLOR][COLOR=#000000]        [/COLOR][COLOR=#5454ff]**spa**[/COLOR][COLOR=#000000] [/COLOR]
_config.yml               [COLOR=#5454ff]**man**[/COLOR][COLOR=#000000]          [/COLOR][COLOR=#5454ff]**pipewire-pulseaudio**[/COLOR][COLOR=#000000]  [/COLOR][COLOR=#5454ff]**src**[/COLOR][COLOR=#000000] [/COLOR]
COPYING                   meson.build  [COLOR=#5454ff]**po**[/COLOR][COLOR=#000000]                   template.test.in [/COLOR]

[/FONT]

---

