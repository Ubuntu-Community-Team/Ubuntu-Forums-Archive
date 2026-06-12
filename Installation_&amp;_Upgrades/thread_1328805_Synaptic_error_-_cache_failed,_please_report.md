---
title: "Synaptic error - cache failed, please report"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by roshi chris on 2009-11-16
I was downloading and installing some stuff from Medibuntu (google earth to be specific) when the installer hung.  I forced it to quit.  When I tried to open synaptic afterwards it wouldn't let me, an error said that another installer was already open (apt-get or aptitute) and wouldn't let me open another.   So I restarted.  Now when i try to open synaptic i get the following popup:


[I]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure-a' to correct the problem.
E: _cache->open() failed, please report.[/I]


I inserted the suggested text into a terminal and got the following:


[I]dpkg: unknown option --configure-a

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' ![/I]


The problem persists.  I have found similar lines mentioned in other errors discussed on the forums but no solution.   I am a newb to linux, straight from the ms tit so not too clued up i'm afraid!

Thanks in advance

Chris

---

### Post by lemming465 on 2009-11-17
There was either a typo or a misinterpretation with the directions, what they were suggestiong was running:```
sudo dpkg  --configure  -a
```
where the **-a** is a second argument to the dpkg command, separated from previous arguments by at least one space.  This is fairly typical of Unix style commands.  See *man dpkg* for the longer version; though until you learn a fair bit about debian style packages those "directions" may be a bit confusing.

Another possible repair sequence is to move one step up the packaging food chain from dpkg, and try:```

sudo -i
apt-get clean   # remove cached downloads
apt-get update  # refresh repository lists
apt-get upgrade --fix-broken  # fancier than the dpkg try
```

---

### Post by roshi chris on 2009-11-19
Thanks Lemming.  I actually left the problem for a couple of days and when I tried again today it seems to have fixed itself.  I know that phrase 'fixed itself' is unhelpful and probably not even possible but nevertheless for some reason the problem has gone!

So thanks anyway, the issue is now closed (though i don't think it counts as Solved)

ta

---

