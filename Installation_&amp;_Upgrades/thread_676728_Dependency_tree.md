---
title: "Dependency tree"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by stiebrs on 2008-01-24
Hi there. 
Im complete newbie to linux, so dont be surprised if i have some wrong ideas/questions ;)
Got kubuntu 6.10 cd, installed, upgraded to 7.10. I'm running it for 3 weeks and i like it...whatever
so, the problem:
running apt-get/aptitude hungs up while "Building dependency tree..50%". Left it for a couple of hours - nothing changed. Rebooting doesn't help (im oldschool windows user ;) ). Now for a couple of days i'm unable to install/update any program.

any solutions/ideas?

p.s. running x386 version

---

### Post by peabody on 2008-01-24
Pretty odd problem.  The honest to goodness only thing I can think to suggest is to run apt-get in a terminal via a program called strace (strace apt-get upgrade).  This should barf a bunch of incomprehensible jargon to the screen, and then hang.  Might be worth then copying and pasting the last little bit of that here.

---

### Post by stiebrs on 2008-01-24
here you go:
all full log is aviable here: [http://box.latnet.lv/kupload/log](http://box.latnet.lv/kupload/log)
```
stat64("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-proposed_main_i18n_Translation-en%5fUS", 0xbf820514) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-proposed_multiverse_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=29304, ...}) = 0
stat64("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-proposed_multiverse_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=29304, ...}) = 0
stat64("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-proposed_multiverse_i18n_Translation-en%5fUS", 0xbf820514) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-proposed_universe_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=125691, ...}) = 0
stat64("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-proposed_universe_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=125691, ...}) = 0
stat64("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-proposed_universe_i18n_Translation-en%5fUS", 0xbf820514) = -1 ENOENT (No such file or directory)
stat64("/var/lib/dpkg/status", {st_mode=S_IFREG|0644, st_size=1336531, ...}) = 0
close(5)                                = 0
gettimeofday({1201173699, 48657}, NULL) = 0
write(1, "\rReading package lists... 100%\r", 31) = 31
write(1, "\rReading package lists... Done\r", 31) = 31
write(1, "\n", 1)                       = 1
mmap2(NULL, 360448, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb702c000
stat64("/etc/apt/preferences", 0xbf81fe94) = -1 ENOENT (No such file or directory)
mmap2(NULL, 839680, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f5f000
mmap2(NULL, 176128, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f34000
write(1, "\rBuilding dependency tree... 0%\r", 32) = 32
write(1, "\rBuilding dependency tree... 0%\r", 32) = 32
gettimeofday({1201173699, 51491}, NULL) = 0
gettimeofday({1201173699, 54250}, NULL) = 0
gettimeofday({1201173699, 55529}, NULL) = 0
gettimeofday({1201173699, 56538}, NULL) = 0
gettimeofday({1201173699, 57514}, NULL) = 0
gettimeofday({1201173699, 58329}, NULL) = 0
gettimeofday({1201173699, 59123}, NULL) = 0
gettimeofday({1201173699, 59892}, NULL) = 0
gettimeofday({1201173699, 60730}, NULL) = 0
gettimeofday({1201173699, 61501}, NULL) = 0
gettimeofday({1201173699, 62257}, NULL) = 0
gettimeofday({1201173699, 63005}, NULL) = 0
gettimeofday({1201173699, 63843}, NULL) = 0
gettimeofday({1201173699, 64589}, NULL) = 0
gettimeofday({1201173699, 65380}, NULL) = 0
gettimeofday({1201173699, 66122}, NULL) = 0
gettimeofday({1201173699, 66972}, NULL) = 0
gettimeofday({1201173699, 67711}, NULL) = 0
gettimeofday({1201173699, 68565}, NULL) = 0
gettimeofday({1201173699, 69452}, NULL) = 0
gettimeofday({1201173699, 70196}, NULL) = 0
gettimeofday({1201173699, 70929}, NULL) = 0
gettimeofday({1201173699, 71758}, NULL) = 0
gettimeofday({1201173699, 72563}, NULL) = 0
gettimeofday({1201173699, 73330}, NULL) = 0
gettimeofday({1201173699, 74065}, NULL) = 0
gettimeofday({1201173699, 74855}, NULL) = 0
gettimeofday({1201173699, 75712}, NULL) = 0
gettimeofday({1201173699, 76451}, NULL) = 0
gettimeofday({1201173699, 77181}, NULL) = 0
gettimeofday({1201173699, 77916}, NULL) = 0
gettimeofday({1201173699, 78782}, NULL) = 0
gettimeofday({1201173699, 79513}, NULL) = 0
gettimeofday({1201173699, 80249}, NULL) = 0
gettimeofday({1201173699, 80977}, NULL) = 0
gettimeofday({1201173699, 81787}, NULL) = 0
gettimeofday({1201173699, 82521}, NULL) = 0
gettimeofday({1201173699, 83245}, NULL) = 0
gettimeofday({1201173699, 83967}, NULL) = 0
gettimeofday({1201173699, 84764}, NULL) = 0
gettimeofday({1201173699, 85490}, NULL) = 0
gettimeofday({1201173699, 86284}, NULL) = 0
gettimeofday({1201173699, 87015}, NULL) = 0
gettimeofday({1201173699, 87826}, NULL) = 0
gettimeofday({1201173699, 88555}, NULL) = 0
gettimeofday({1201173699, 89370}, NULL) = 0
gettimeofday({1201173699, 90113}, NULL) = 0
gettimeofday({1201173699, 90924}, NULL) = 0
gettimeofday({1201173699, 91658}, NULL) = 0
gettimeofday({1201173699, 92394}, NULL) = 0
write(1, "\rBuilding dependency tree... 50%"..., 33) = 33
write(1, "\rBuilding dependency tree... 50%"..., 33) = 33
gettimeofday({1201173699, 93445}, NULL) = 0
gettimeofday({1201173699, 103954}, NULL) = 0
gettimeofday({1201173699, 112722}, NULL) = 0
gettimeofday({1201173699, 122638}, NULL) = 0
gettimeofday({1201173699, 133098}, NULL) = 0
gettimeofday({1201173699, 142123}, NULL) = 0
gettimeofday({1201173699, 152287}, NULL) = 0
gettimeofday({1201173699, 160448}, NULL) = 0
gettimeofday({1201173699, 168474}, NULL) = 0
gettimeofday({1201173699, 176046}, NULL) = 0
gettimeofday({1201173699, 185438}, NULL) = 0
gettimeofday({1201173699, 193787}, NULL) = 0
gettimeofday({1201173699, 218119}, NULL) = 0
gettimeofday({1201173699, 226404}, NULL) = 0
gettimeofday({1201173699, 235348}, NULL) = 0
gettimeofday({1201173699, 244378}, NULL) = 0
gettimeofday({1201173699, 252354}, NULL) = 0
--- SIGINT (Interrupt) @ 0 (0) ---
+++ killed by SIGINT +++
```

---

### Post by peabody on 2008-01-24
Hmm, out of curiosity, how's the clock on your machine...set to current time?

Did you kill the program with Ctrl+C yourself, or did it die of its own volition?

---

### Post by stiebrs on 2008-01-24
i killed it after a while
system time is correct and set to local timezone

can i offer some other logs that can be of use?

i'll leave strace for a longer time to see, will it keep trying to "gettimeofday"

---

### Post by stiebrs on 2008-01-24
and here goes output of "sudo strace -o log2 apt-get install proftpd" running for a couple of hours (since my last post). full log is aviable [here]("http://box.latnet.lv/kupload/log2")

```
stat64("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-proposed_universe_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=125691, ...}) = 0
stat64("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-proposed_universe_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=125691, ...}) = 0
stat64("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-proposed_universe_i18n_Translation-en%5fUS", 0xbfbdf174) = -1 ENOENT (No such file or directory)
stat64("/var/lib/dpkg/status", {st_mode=S_IFREG|0644, st_size=1336531, ...}) = 0
close(5)                                = 0
gettimeofday({1201176088, 315346}, NULL) = 0
write(1, "\rReading package lists... 100%\r", 31) = 31
write(1, "\rReading package lists... Done\r", 31) = 31
write(1, "\n", 1)                       = 1
mmap2(NULL, 360448, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ff1000
stat64("/etc/apt/preferences", 0xbfbdeaf4) = -1 ENOENT (No such file or directory)
mmap2(NULL, 839680, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f24000
mmap2(NULL, 176128, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ef9000
write(1, "\rBuilding dependency tree... 0%\r", 32) = 32
write(1, "\rBuilding dependency tree... 0%\r", 32) = 32
gettimeofday({1201176088, 345459}, NULL) = 0
gettimeofday({1201176088, 349330}, NULL) = 0
gettimeofday({1201176088, 350966}, NULL) = 0
gettimeofday({1201176088, 352373}, NULL) = 0
gettimeofday({1201176088, 353489}, NULL) = 0
gettimeofday({1201176088, 354512}, NULL) = 0
gettimeofday({1201176088, 355586}, NULL) = 0
gettimeofday({1201176088, 356552}, NULL) = 0
gettimeofday({1201176088, 357522}, NULL) = 0
gettimeofday({1201176088, 358551}, NULL) = 0
gettimeofday({1201176088, 359531}, NULL) = 0
gettimeofday({1201176088, 360564}, NULL) = 0
gettimeofday({1201176088, 361623}, NULL) = 0
gettimeofday({1201176088, 362664}, NULL) = 0
gettimeofday({1201176088, 363704}, NULL) = 0
gettimeofday({1201176088, 364725}, NULL) = 0
gettimeofday({1201176088, 365726}, NULL) = 0
gettimeofday({1201176088, 366733}, NULL) = 0
gettimeofday({1201176088, 367759}, NULL) = 0
gettimeofday({1201176088, 368668}, NULL) = 0
gettimeofday({1201176088, 369588}, NULL) = 0
gettimeofday({1201176088, 370575}, NULL) = 0
gettimeofday({1201176088, 371494}, NULL) = 0
gettimeofday({1201176088, 372409}, NULL) = 0
gettimeofday({1201176088, 373507}, NULL) = 0
gettimeofday({1201176088, 374429}, NULL) = 0
gettimeofday({1201176088, 375344}, NULL) = 0
gettimeofday({1201176088, 376377}, NULL) = 0
gettimeofday({1201176088, 377304}, NULL) = 0
gettimeofday({1201176088, 378221}, NULL) = 0
gettimeofday({1201176088, 379205}, NULL) = 0
gettimeofday({1201176088, 380213}, NULL) = 0
gettimeofday({1201176088, 381134}, NULL) = 0
gettimeofday({1201176088, 382064}, NULL) = 0
gettimeofday({1201176088, 383068}, NULL) = 0
gettimeofday({1201176088, 383977}, NULL) = 0
gettimeofday({1201176088, 384891}, NULL) = 0
gettimeofday({1201176088, 385914}, NULL) = 0
gettimeofday({1201176088, 386860}, NULL) = 0
gettimeofday({1201176088, 387768}, NULL) = 0
gettimeofday({1201176088, 388833}, NULL) = 0
gettimeofday({1201176088, 390596}, NULL) = 0
gettimeofday({1201176088, 391687}, NULL) = 0
gettimeofday({1201176088, 392631}, NULL) = 0
gettimeofday({1201176088, 393575}, NULL) = 0
gettimeofday({1201176088, 394515}, NULL) = 0
gettimeofday({1201176088, 395598}, NULL) = 0
gettimeofday({1201176088, 396515}, NULL) = 0
gettimeofday({1201176088, 398961}, NULL) = 0
gettimeofday({1201176088, 400181}, NULL) = 0
write(1, "\rBuilding dependency tree... 50%"..., 33) = 33
write(1, "\rBuilding dependency tree... 50%"..., 33) = 33
gettimeofday({1201176088, 401603}, NULL) = 0
gettimeofday({1201176088, 415924}, NULL) = 0
gettimeofday({1201176088, 443150}, NULL) = 0
gettimeofday({1201176088, 456533}, NULL) = 0
gettimeofday({1201176088, 472312}, NULL) = 0
gettimeofday({1201176088, 484403}, NULL) = 0
gettimeofday({1201176088, 502280}, NULL) = 0
gettimeofday({1201176088, 510538}, NULL) = 0
gettimeofday({1201176088, 518695}, NULL) = 0
gettimeofday({1201176088, 526382}, NULL) = 0
gettimeofday({1201176088, 535847}, NULL) = 0
gettimeofday({1201176088, 544171}, NULL) = 0
gettimeofday({1201176088, 553926}, NULL) = 0
gettimeofday({1201176088, 562414}, NULL) = 0
gettimeofday({1201176088, 571382}, NULL) = 0
gettimeofday({1201176088, 580434}, NULL) = 0
gettimeofday({1201176088, 588497}, NULL) = 0
--- SIGINT (Interrupt) @ 0 (0) ---
+++ killed by SIGINT +++
```


p.s. Killed it myself

---

