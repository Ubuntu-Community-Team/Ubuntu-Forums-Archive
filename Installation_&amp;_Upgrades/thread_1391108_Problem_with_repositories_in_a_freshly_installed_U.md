---
title: "Problem with repositories in a freshly installed Ubuntu Karmic"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by calsaverini on 2010-01-26
I have a freshly installed Ubuntu Karmic 32 bits installed in an old machine (Pentium 4 512 Mb RAM) and I'm having a severe problem with apt-get. 

No matter what repository I choose, I can't update the repository files. I get the following error during a ```
apt-get update
```:

```

Hit http://br.archive.ubuntu.com karmic-updates/universe Sources                                                                       
Hit http://br.archive.ubuntu.com karmic-updates/multiverse Packages                                                                    
Hit http://br.archive.ubuntu.com karmic-updates/multiverse Sources                                                                     
96% [4 Sources bzip2 10792960]                                                                                                    120kB/s 2s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://br.archive.ubuntu.com karmic/universe Sources                                                                                    
  Sub-process /bin/bzip2 returned an error code (2)
Downloaded 7920kB em 58s (136kB/s)                                                                                                            
W: Failed while searching http://br.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

```I have another computer in the same network that is perfectly able do download those files and update it's package database. 

Also, when I try to install any package with apt-get I get a "incorrect hash sum":
```

E: Failed retrieving http://br.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.2.245-2ubuntu2_all.deb: incorrect Hash Sum 


```Again: I have a computer in the same network that can install any package normally, so it's not a local network problem.

Does anyone have any clue in what can be happening? I tried many different repositories. 

I also had a problem installing Grub in this machine (had to resort to LILO, cause Grub wouldn't install). Can this be a hardware problem?

---

### Post by calsaverini on 2010-01-28
Tested my memory with the memtest and my harddrive with e2fsck -c. Apparently not a hardware or network problem. I thought it should be a hardware problem but I'm not sure anymore.

To simplify the error messages I kept only the main repository. This is my current sources.list:

```

## See sources.list(5) for more information, especialy
# Remember that you can only use http, ftp or file URIs
deb http://archive.linux.duke.edu/ubuntu/ karmic main
# CDROMs are managed through the apt-cdrom tool.

```

(I've tried DOZENS of different repositories, including the main repo).

When I run ```
sudo apt-get update
``` I get the following:

```

anapaola@tarugo:~$ sudo apt-get update
Hit http://archive.ubuntu.com karmic Release.gpg
Ign http://archive.ubuntu.com karmic/main Translation-en_US
Hit http://archive.ubuntu.com karmic Release
Get:1 http://archive.ubuntu.com karmic/main Packages [1,353kB]
99% [1 Packages bzip2 0]                                                                                                         15.2kB/s 0s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com karmic/main Packages                                                                                          
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 1,023kB in 59s (17.3kB/s)                                                                                                           
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by phillw on 2010-01-28
Hmmm... odd one.

Have you tried
```
sudo dpkg --configure -a 
```

to see if it has gotten a bit 'confused' ?

Regards,

Phill.

---

