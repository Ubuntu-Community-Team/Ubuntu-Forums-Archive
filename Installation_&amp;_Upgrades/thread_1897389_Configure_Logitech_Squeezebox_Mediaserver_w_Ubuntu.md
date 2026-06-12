---
title: "Configure Logitech Squeezebox Mediaserver w/ Ubuntu 11.10"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by simistef on 2011-12-19
Hi guys,

I have installed Ubuntu 11.10, and try now to configure Logitech Media Server. I have downloaded the deb file form mysqueezebox.com version 7.7.1 run it and installed it successfully since i am able to access the Squeezebox panel : [http://localhost:900](http://localhost:900).

I am facing two problems :

1. I have 2 internal hard drives installed, both formatted with ext4. One is primary and one is secondary. On the web interface of squeezebox, when trying to add music to the library, i cannot see the second disk. When browsing to /media/ folder it is empty. If i am browsing from ubuntu, i can see inside /media/disk2/Music.

This probably relates to a note from Logitech's site for installation : 
NOTE: You must give the Squeezebox Server account proper permissions to access your music library and playlists.

How can i do that ? I cannot see the Squeezebox server account. I can only see my account.

2. If i add music in the /home/mediaserver/Music folder, i can see it in the application, but the Squeezebox fails to add the music in the library.

Here is a snippet from the server log file :

```
[11-12-19 11:55:45.9951] main::main (200) Starting Logitech Media Server scanner (v7.7.1, r33735, Mon Nov 28 15:45:08 PST 2011) perl 5.012004
[11-12-19 11:55:46.4168] Slim::Schema::forceCommit (2118) Warning: Trying to commit transactions before DB is initialized!
[11-12-19 11:55:46.6294] Slim::Music::Import::runImporter (485) Starting Slim::Media::MediaFolderScan scan
[11-12-19 11:55:46.6308] Slim::Utils::Scanner::Local::rescan (171) Discovering audio files in /home/mediaserver/Music
[11-12-19 11:55:46.7837] Slim::Utils::Scanner::Local::__ANON__ (254) Removing deleted audio files (0)
[11-12-19 11:55:46.7843] Slim::Utils::Scanner::Local::__ANON__ (332) Scanning new audio files (0)
[11-12-19 11:55:46.7847] Slim::Utils::Scanner::Local::__ANON__ (410) Rescanning changed audio files (0)
[11-12-19 11:55:46.9060] Slim::Utils::Scanner::LMS::__ANON__ (245) ERROR SCANNING /home/mediaserver/Music/Very.Best.Smooth.Jazz.2/VA-The_Very_Best_of_Smooth_Jazz_Vol._2.jpg: Unable to open file for reading(code -3)
[11-12-19 11:55:46.9068] Slim::Utils::Scanner::LMS::__ANON__ (260) Scanning new media files (1)
```

So has an error on scanning. Anyone can help me with this please ? 

Thank you in advance !

---

### Post by bjbwood on 2012-01-07
I have exactly the same problem with scanning....will only opick up actual files in Music directory - tried home, my personal folder and public.

New install of Ubuntu and LMS on a very cure HP MicroServer.....

Ben

---

