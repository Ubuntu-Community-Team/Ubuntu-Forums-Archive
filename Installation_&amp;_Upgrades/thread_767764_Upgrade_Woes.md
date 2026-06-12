---
title: "Upgrade Woes"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by supernovus on 2008-04-25
Well, I can finally say I've had breakage in an Ubuntu upgrade!

The surprising part is, this is also the first time I waited until the release was, well, released.  I almost always upgrade 1 to 2 months before the release is official. This time I waited. 

Now I'm having a few issues. Only a few, but fairly major ones considering this computer is used for music and videos.

First off, Xine claims it can't connect to the sound server. I'm assuming that's a PuleAudio issue. Wouldn't be a problem except that Xine is the only app I have configured to work with my Lirc remote so far.  

Anyway, Rhythmbox doesn't work either, it claims that it doesn't have the CODECs to play anything. Doesn't matter what it is, ogg, mp3, flac, none of my music is playable anymore. It tries to search for a CODEC to fix the issue, but doesn't find any. I have all of the gstreamer0.10- packages installed (except the -dev and -dbg ones) so I can't see what it's going on about.

The Totem Movie Player doesn't work at all either. It says it "can't locate the resource" when I try to get it to play a video or audio file. Very odd.

The volume control thingy still works, and I know that it's not a kernel driver issue, as VLC works fine (with all my video and audio files).

I'm going to play with it for a while to see what I can find, if anyone has any advise, let me know. I'm going to try blasting away a bunch of dot directories and see what effect it has.

Anyway, on a positive note, Hardy seems much faster than the last few versions, and I really like the PolicyKit implementation and Firefox 3.

---

### Post by Pumalite on 2008-04-25
Install:
sudo apt-get install ubuntu-restricted-extras
If you still have troubles, post back.

---

### Post by supernovus on 2008-04-25
I already had ubuntu-restricted-extras installed. 

Anyway, I cleared out all of my .dotfile-directories, so-as to basically reboot my account. System sounds work now.

So far, a few things.

1) Totem works, although slow. So does Xine, also slow and slightly jerky, but at least it works now. VLC also has slowed down. All of them seem to lag the worst when switching between Windowed and Full Screen.

2) Rhythmbox, oh this is the most lovely of them all. It works, but only with files that don't have spaces in their names. Anything with a space, it cannot load, claiming "file not found". Which is a problem, as 95% of the songs I have, use spaces in the filenames. I'd assume this to be a GVFS problem, except that Nautilus audio preview works and so does Totem with the very same files.

3) There is no 3.

I'll report back with more info as I come across it.

---

### Post by supernovus on 2008-04-26
Well, I found a workaround to the Rhythmbox issue, although the underlying bug is still there.

Basically, if your /home/username/Music folder is actually a symbolic link to a different directory, when Rhythmbox tries to follow the links, it fails if they have spaces in the names. It didn't do this in the Gutsy version, so it may be a GVFS issue that just isn't showing up in other apps.

The workaround? Remove all the songs in your list, then change the Library folder to the real location, not the symlink. Reload RB and it rebuilds your music collection.

I also had an issue with my SB Live! card not playing audio out of the second output jack (Wave Surround), but found pacontrol [http://ubuntuforums.org/showthread.php?t=759147](http://ubuntuforums.org/showthread.php?t=759147) and after selecting the correct settings in that and logging back in, that fixed the issue.

So, a few more bugs than usual, but nothing that wasn't fixable. Let Hardy roar!

---

### Post by supernovus on 2008-05-02
Well, I'm back. Remember how I said that Hardy was faster than the previous versions? This still applies on my work computer, where I have had no upgrade issues at all, but on my home computer (where are the problems I noted above occurred), my computer is really bloody slow! Unbearably so. 

I cannot even play videos at the proper speed anymore. I have no idea what is going on.

I'm thinking it may be time to back up my files, and reinstall from scratch. This install has been upgraded from Edgy->Fesity->Gutsy->Hardy... the previous install I had worked great from Warty->Hoary->Breezy->Dapper and then when I tried to upgrade from Dapper->Edgy, I had similar issues to what I am having now, so I reinstalled from scratch.

This speed issue is very strange, so I hope that reinstalling fixes it.

If anyone has any advice on speeding up Hardy (or Ubuntu in general), let me know. I'll post anything I find on here, and will let you know the results of the clean install.

---

