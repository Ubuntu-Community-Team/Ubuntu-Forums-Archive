---
title: "Update Manager error: Untrusted packages"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by Ben_G_9C9 on 2010-11-12
A few weeks ago, i installed Ubuntu Desktop 10.10. I installed several of my previously used programs and am now having trouble with the update manager. It refuses to download updates; insisting that it does not trust the source. The details in the error message indicate that the problem is with a package for Banshee Media Player.

I am posting a link for a video I made that displays this problem.
[http://www.justin.tv/beng_9c9/b/273720942](http://www.justin.tv/beng_9c9/b/273720942)

---

### Post by sikander3786 on 2010-11-12
Go to Software Center > Edit > Software Sources and change your server to Main. Now open terminal (Applications > Accessories > Terminal) and try these commands and post the output

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by Ben_G_9C9 on 2010-11-12
The UPDATES command failed. 

```
Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://extras.ubuntu.com maverick/main Sources/DiffIndex                   
Ign http://extras.ubuntu.com maverick/main i386 Packages/DiffIndex             
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Fetched 198B in 11s (18B/s)                                                    
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

The UPGRADE Command finished normally.

---

### Post by sikander3786 on 2010-11-12
I think it is something related to the GPG keys however it is referring to hostname resolution.

You can try adding the missing GPG by

```
gpg --keyserver keyserver.ubuntu.com --recv 16126D3A3E5C1192
```

```
gpg --export --armor 16126D3A3E5C1192 | sudo apt-key add -
```

The second one should say OK.

Now try

```
sudo apt-get update
```

---

### Post by Ben_G_9C9 on 2010-11-12
The first two codes worked without error. The Second one did simply say "OK".

On the UPDATE command, I got the same error.

```
Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://archive.canonical.com maverick Release                              
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex      
Hit http://archive.canonical.com maverick/partner i386 Packages                
Fetched 65B in 10s (6B/s)                                                      
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by rondackcpu on 2010-11-12
The error messages you have in the last two boxes are minor problems with the "update" process, not the "upgrade" process.  The error statements mean only that the referenced repositories have not been located by your ISP's address resolver.  Indeed, they may not exist.  To suppress the error messages, edit the </etc/apt/sources.list> file so as to ignore the lines containing the bad addresses (that is, put a # in front of the line(s) to "comment it(them) out").

The upgrade process will go along just fine if (when) you issue the "sudo apt-get upgrade" or "sudo aptitude safe-upgrade" command in the terminal whether or not you comment out the bad addresses.

Running "update" again may not tell you that there are new updates available because it has already told you about the ones found when you first typed an update command long ago.  There may not be any newer  ones since then.  Just go ahead and upgrade with either of those commands.

CRS

---

