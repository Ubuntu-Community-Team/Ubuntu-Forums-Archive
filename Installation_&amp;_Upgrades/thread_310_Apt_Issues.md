---
title: "Apt Issues"
date: 2004-10-12
forum: Installation &amp; Upgrades
---

### Post by Anonymous on 2004-10-12
I'm a pretty new Linux user, so feel free to chastise me if this is a stupid question.

I'm trying to install new software and make my shiny new Ubuntu distro work, but apt refuses to refresh its repositories. My sources.list is the standard, this is the terminal behaviour:

```
matt@tenebrus ~ $ sudo apt-get update
Get&#58;1 http&#58;//archive.ubuntu.com warty/main Packages &#91;2142kB&#93;
Err http&#58;//archive.ubuntu.com warty/main Packages
  Error reading from server - read &#40;104 Connection reset by peer&#41;
Get&#58;2 http&#58;//archive.ubuntu.com warty/main Release &#91;79B&#93;
Get&#58;3 http&#58;//archive.ubuntu.com warty/restricted Packages &#91;21.3kB&#93;
0% &#91;3 Packages gzip 0&#93; &#91;Waiting for headers&#93;                       39.2kB/s 54s
gzip&#58; stdin&#58; not in gzip format
Err http&#58;//archive.ubuntu.com warty/restricted Packages
  Sub-process gzip returned an error code &#40;1&#41;
Get&#58;4 http&#58;//archive.ubuntu.com warty/restricted Release &#91;85B&#93;
Get&#58;5 http&#58;//archive.ubuntu.com warty/main Sources &#91;685kB&#93;
24% &#91;5 Sources gzip 0&#93; &#91;Waiting for headers&#93;                       64.2kB/s 33s
gzip&#58; stdin&#58; not in gzip format
Err http&#58;//archive.ubuntu.com warty/main Sources
  Sub-process gzip returned an error code &#40;1&#41;
Get&#58;6 http&#58;//archive.ubuntu.com warty/main Release &#91;81B&#93;
Get&#58;7 http&#58;//archive.ubuntu.com warty/restricted Sources &#91;3159B&#93;
24% &#91;7 Sources gzip 0&#93; &#91;Waiting for headers&#93;                                                                 64.2kB/s 33s
gzip&#58; stdin&#58; not in gzip format
Err http&#58;//archive.ubuntu.com warty/restricted Sources
  Sub-process gzip returned an error code &#40;1&#41;
Get&#58;8 http&#58;//archive.ubuntu.com warty/restricted Release &#91;87B&#93;
Fetched 709kB in 57s &#40;12.2kB/s&#41;
Failed to fetch http&#58;//archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz  Error reading from server - read &#40;104 Connection reset by peer&#41;
Failed to fetch http&#58;//archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz  Sub-process gzip returned an error code &#40;1&#41;
Failed to fetch http&#58;//archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz  Sub-process gzip returned an error code &#40;1&#41;
Failed to fetch http&#58;//archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz  Sub-process gzip returned an error code &#40;1&#41;
Reading Package Lists... Done
W&#58; Couldn't stat source package list http&#58;//archive.ubuntu.com warty/main Packages &#40;/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_main_binary-i386_Packages&#41; - stat &#40;2 No such file or directory&#41;
W&#58; Couldn't stat source package list http&#58;//archive.ubuntu.com warty/restricted Packages &#40;/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages&#41; - stat &#40;2 No such file or directory&#41;
W&#58; You may want to run apt-get update to correct these problems
E&#58; Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas?

Thanks,
Matt

---

### Post by adbak on 2004-10-14
I'm probably as much of a newb as you are, but it looks like you're using the regular terminal.  I'm not quite up to date on sudo,  but you might want to try typing 'apt-get update' in your root terminal instead of your normal terminal.

Either that or check your internet connection.

Sorry I couldn't be of more help.

---

