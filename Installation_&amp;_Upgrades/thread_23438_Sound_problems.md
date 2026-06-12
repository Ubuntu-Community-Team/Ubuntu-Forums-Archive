---
title: "Sound problems"
date: 2005-04-01
forum: Installation &amp; Upgrades
---

### Post by Gandalf on 2005-04-01
hello, (i'm back again :D )
well i have a problemwith my sound card, a little info on my PC:
HP pavilion dv1071ea with 80GB HDD and built in ((intel) sound card
whn i run somehing in ubunutu i hear the sound (poke.....) but i tried to listen to an MP3/Video file and no sound was out :o

---

### Post by clb137 on 2005-04-02
can we have a little more detail on the problem, IE do you have any sound? what program are you useing?

---

### Post by Gandalf on 2005-04-02
[QUOTE=clb137]can we have a little more detail on the problem, IE do you have any sound? what program are you useing?[/QUOTE]
 well, the ubuntu sounds (when you click in the menus etc.... or login/log out) are working perfectly which is so weird
i tried to play mp3 video clips in both VLC and TOTEM, VLC just begin playing without any sound
TOTEM give a warning/error for both MP3 and Video about unsupported/unavailable codec

thanks

---

### Post by Gandalf on 2005-04-02
i tried with Rythmbox including a folder, for all the MP3 file i get the following error:
"there's no plugin installed to handel a MP3 file".
in ubuntu, the MP3/AVI codec are not installed by default :o :roll: ?

//EDIT: i tried the integrated Radio in this program, works perfectly sound is loud and good, so codec missing, can i know the codec package to install with apt-get??? thx in advance

---

### Post by bored2k on 2005-04-02
[QUOTE=Gandalf]i tried with Rythmbox including a folder, for all the MP3 file i get the following error:
"there's no plugin installed to handel a MP3 file".
in ubuntu, the MP3/AVI codec are not installed by default :o :roll: ?

//EDIT: i tried the integrated Radio in this program, works perfectly sound is loud and good, so codec missing, can i know the codec package to install with apt-get??? thx in advance[/QUOTE]
 The problem is called "you did not read the manual" syndrome.
Read [http://ubuntuguide.org/temp/#extrarepositories](http://ubuntuguide.org/temp/#extrarepositories)

Then install gstreamer0.8-mad. For other players like xmms, beep media player, make sure in their setup you make them use esound or esd audio [this goes for audio and video programs].

[http://ubuntuforums.org/showthread.php?t=20588&highlight=hoary+sound](http://ubuntuforums.org/showthread.php?t=20588&highlight=hoary+sound)

[RIGHT]*[SIZE=1]you told me help you, I did ;).[/SIZE]* [/RIGHT]

---

### Post by Gandalf on 2005-04-02
ok done that, TOTEM play only audio now, he don't play video and i can't find any way to set the output, he plays MP3 files
VLC plays only the video without a sound and so fast, in the error log of VLC i see:
```

main error: couldn't find a filter for the conversion
main error: couldn't set an output pipeline

```

i'm looking to the link you added at the end of the post

---

### Post by Gandalf on 2005-04-02
YOU ARE THE MAN :D
thanks it's working now, stay in touch bored2k

---

### Post by bored2k on 2005-04-02
[QUOTE=Gandalf]ok done that, TOTEM play only audio now, he don't play video and i can't find any way to set the output, he plays MP3 files
VLC plays only the video without a sound and so fast, in the error log of VLC i see:
```

main error: couldn't find a filter for the conversion
main error: couldn't set an output pipeline

```

i'm looking to the link you added at the end of the post[/QUOTE]
 Do yourself a favor, before you try anything, let ubuntu-geek [a.k.a. the administrator] help you with this automatic script for new hoary installs: [http://ubuntuforums.org/showthread.php?t=22646&highlight=script](http://ubuntuforums.org/showthread.php?t=22646&highlight=script) . This will save you arguably hours of looking around. After you do so, come back ;) .

---

### Post by bored2k on 2005-04-02
[QUOTE=Gandalf]YOU ARE THE MAN :D
thanks it's working now, stay in touch bored2k[/QUOTE]
 Me? keep in touch? [Here to stay](http://www.azlyrics.com/lyrics/korn/heretostay.html).

P.S. - I have to help, you have like weird freaky powers and stuff with that cane of yours ;) .

---

### Post by Gandalf on 2005-04-02
[QUOTE=bored2k]Me? keep in touch? [Here to stay](http://www.azlyrics.com/lyrics/korn/heretostay.html).

P.S. - I have to help, you have like weird freaky powers and stuff with that cane of yours ;) .[/QUOTE]
[img]http://www.siemens-mobiles.org/forum/Smileys/default/rofl.gif[/img] yea right :D  [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img]

---

### Post by bored2k on 2005-04-02
[QUOTE=Gandalf][img]http://www.siemens-mobiles.org/forum/Smileys/default/rofl.gif[/img] yea right :D  [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img][/QUOTE]
 LOL you're using smileys from your S-M website. Funny ^_^ .

---

### Post by Gandalf on 2005-04-03
[QUOTE=bored2k]LOL you're using smileys from your S-M website. Funny ^_^ .[/QUOTE]
 yes lol i like my smilie set, [img]http://www.siemens-mobiles.org/forum/Smileys/default/angel8.gif[/img] ^^ :D

---

### Post by clb137 on 2005-04-03
very nice Gandalf

---

### Post by Gandalf on 2005-04-03
[QUOTE=clb137]very nice Gandalf[/QUOTE]
 thank you

---

