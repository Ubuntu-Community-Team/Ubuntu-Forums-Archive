---
title: "Problems with dist-upgrade to feisty on T60"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by ask158 on 2007-06-01
I had a perfectly working edgy on my T60 thinkpad. Yesterday I dist-upgraded this to feisty and since have been facing the following problem. The upgrade worked fine until when I got an error message after logging on: "Panel encountered a problem with loading OAFIID:GNOME_MixerApplet",  I ignored the message and noticed that since then, on certain logins, I find that the system becomes very slow to respond. For example starting a terminal takes a minute. Additionally, to start something like 'gvim' from the terminal takes a long time. To investigate the problem I did 'strace' on gvim to find where the stalling occurs. Below is pasted a part of the strace output around the region where the program stalls (I induced newline spaces exactly where it stalls for your convenience):
=======================================================
munmap(0xb6bbc000, 4096)                = 0
write(4, "\0\2\1\1\6\0\0\0\0\0\0\0\0\0\0\0\3\0MIT\0\0\0\3\0001.0"..., 56) = 56
read(4, "\0\3\0\267\1\0\0\0", 8)        = 8
read(4, "\0\0\0\0\0\0\0\0", 8)          = 8
access("/home/arun/.ICEauthority", R_OK) = 0
open("/home/arun/.ICEauthority", O_RDONLY) = 5
fstat64(5, {st_mode=S_IFREG|0600, st_size=169, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6bbc000
read(5, "\0\4XSMP\0\0\0%local/supramental:/tmp"..., 4096) = 169
close(5)                                = 0
munmap(0xb6bbc000, 4096)                = 0
write(4, "\0\4\1\1\3\0\0\0\20\0\0\0\0\0\0\0\262\"j\f\373j\234\204"..., 32) = 32
read(4, "\0\6\0\267\2\0\0\0", 8)        = 8
read(4, "\3\0MIT\0\0\0\3\0001.0\0\0\0", 16) = 16
access("/home/arun/.ICEauthority", R_OK) = 0
open("/home/arun/.ICEauthority", O_RDONLY) = 5
fstat64(5, {st_mode=S_IFREG|0600, st_size=169, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6bbc000
read(5, "\0\4XSMP\0\0\0%local/supramental:/tmp"..., 4096) = 169
read(5, "", 4096)                       = 0
close(5)                                = 0
munmap(0xb6bbc000, 4096)                = 0
write(4, "\0\7\1\0\7\0\0\0\1\1\0\0\0\0\0\0\4\0XSMP\234\204\3\0MI"..., 64) = 64
read(4, "\0\3\0\267\1\0\0\0", 8)        = 8
read(4, "\0\0MIT\0\0\0", 8)             = 8
access("/home/arun/.ICEauthority", R_OK) = 0
open("/home/arun/.ICEauthority", O_RDONLY) = 5
fstat64(5, {st_mode=S_IFREG|0600, st_size=169, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6bbc000
read(5, "\0\4XSMP\0\0\0%local/supramental:/tmp"..., 4096) = 169
close(5)                                = 0
munmap(0xb6bbc000, 4096)                = 0
write(4, "\0\4\1\0\3\0\0\0\20\0\0\0\0\0\0\0\262\"j\f\373j\234\204"..., 32) = 32
read(4, "\0\10\0\1\3\0\0\0", 8)         = 8
read(4, "\7\0GnomeSM\0001.\6\0002.18.0\0\0\0\0", 24) = 24
write(4, "\1\1\1\0\1\0\0\0\0\0\0\0\0\0\0\0", 16) = 16
read(4, 
















"\1\2\0\1\6\0\0\0", 8)          = 8
read(4, "%\0\0\000103f51c730000118071009600000"..., 48) = 48
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
access("/home/arun/.terminfo/x/xterm", R_OK) = -1 ENOENT (No such file or directory)
access("/etc/terminfo/x/xterm", R_OK)   = -1 ENOENT (No such file or directory)
access("/lib/terminfo/x/xterm", R_OK)   = 0
open("/lib/terminfo/x/xterm", O_RDONLY|O_LARGEFILE) = 5
read(5, "\32\1\34\0\35\0\17\0\235\1&\5", 12) = 12
read(5, "xterm|X11 terminal emulator\0", 28) = 28
read(5, "\0\1\0\0\1\0\0\0\1\0\0\0\0\1\1\0\0\0\0\0\0\0\1\0\0\1\0"..., 29) = 29
read(5, "\0", 1)                        = 1
read(5, "P\0\10\0\30\0\377\377\377\377\377\377\377\377\377\377\377"..., 30) = 30
read(5, "\0\0\4\0\6\0\10\0\31\0\36\0&\0*\0.\0\377\3779\0J\0L\0P"..., 826) = 826
read(5, "\33[Z\0\7\0\r\0\33[%i%p1%d;%p2%dr\0\33[3g\0\33["..., 1318) = 1318
read(5, "", 10)                         = 0
close(5)                                = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=44, ws_col=141, ws_xpixel=0, ws_ypixel=0}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=44, ws_col=141, ws_xpixel=0, ws_ypixel=0}) = 0
brk(0x826f000)                          = 0x826f000
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=44, ws_col=141, ws_xpixel=0, ws_ypixel=0}) = 0
open(".", O_RDONLY)                     = 5
fchdir(5)                               = 0
chdir("/usr/share/vim")                 = 0
getcwd("/usr/share/vim", 1024)          = 15
fchdir(5)                               = 0
close(5)                                = 0
==========================================================

I initially thought the problem was with .ICEauthority file. On deleting the .ICEauthority  in my home directory and logging in again, I find the problem gone. But this is not always the case.  I am beginning to think that the problem occurs when my laptop is not connect to the  internet (wired or wireless). This problem occurs consistently when I am not connected.

I hope I stated clearly my problem. I request all the GODS here on the forum to please suggest me a way out of this problem.

Thanks in advance.

---

