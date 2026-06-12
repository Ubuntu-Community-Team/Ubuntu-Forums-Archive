---
title: "Thunderbird segfault in Lucid"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by escozzia on 2010-08-24
I have a pretty standard home setup, everything is on a single partition, only one user (besides root) and thunderbird refuses to start, giving me a segmentation fault and nothing else. So far I've tried removing and reinstalling, installing nscd (I know, it's got nothing to do, but I had nothing to lose),  compiling from source, and removing ~/.thunderbird and ~/.mozilla-thunderbird as well as changing their permissions.
Binaries downloaded from the website don't give me the segfault, but instead load up the "thunderbird has crashed" window.
I tried running it as root and it worked, but I don't think that's a good idea under any circumstances.
Weird thing is it worked perfectly like 3 days ago, and I haven't changed anything since then (I think I did an update though, I'll check on that)
Seamonkey is the same thing, it quits with a segfault as soon as I launch it...
I'm really going crazy here, so any help would be really appreciated
Uhm by the way, I'm new here so I'm not sure if this thread belongs here, if it doesn't I'm really sorry, feel free to move it around.

---

### Post by quixote on 2010-08-25
Have you tried installing it using synaptic?  Installing from binaries, let alone source code, is at least for me always a much iffier process.  Whereas if done from synaptic it's usually bulletproof.  Also, after the "thunderbird has crashed" stuff, can you cancel or ignore that message and will it start up?  Or does it just keep doing nothing but the crash message?

---

### Post by escozzia on 2010-08-25
Hey Quixote, thanks for the reply :)
Unfortunately, installs from synaptic don't work either, they just quit with the segfault.
Also, I'm afraid I can't bypass the error messages, they only give me the option to restart thunderbird (with the same result) or quitting...

---

### Post by quixote on 2010-08-26
So, no easy answers :(.  Bah.  And humbug.  I don't know what the real solution is.  I'd flail around as follows: 

If you have mail that you want to backup so you can get at it again once Thunderbird is finally working, then copy this directory to another location: /home/*[COLOR="Blue"]your-user[/COLOR]*/.mozilla-thunderbird/*[COLOR="Blue"]alphanumeric-gobbledygook[/COLOR]*.default/Mail.  Once it's running, I'd just copy the contents into the new .default/Mail.

Uninstall thunderbird in synaptic using the remove-completely or purge option.  Delete the .mozilla-thunderbird directory in your /home dir. That will remove all your settings, themes, and so on, but since one of those might be what's causing the conflict, I'd do it anyway, if it were me.

Then try reinstalling via synaptic.

Again, I have no idea whether that would do any good.  It's just what I'd try.

---

### Post by escozzia on 2010-08-26
Hey, thanks again for the reply.
I tried what you said, but unfortunately, it still doesn't work :'(
I'm clueless, this is really strange, guess I'll file a bug report and wait for them to fix it...

---

### Post by escozzia on 2010-08-26
I just did a "strace thunderbird", now, I can't read too much into this myself, but maybe someone may find it useful:
```

execve("/usr/bin/thunderbird", ["thunderbird"], [/* 46 vars */]) = 0
brk(0)                                  = 0x9cbc000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78a0000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=93647, ...}) = 0
mmap2(NULL, 93647, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7889000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000m\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1405508, ...}) = 0
mmap2(NULL, 1415592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb772f000
mprotect(0xb7882000, 4096, PROT_NONE)   = 0
mmap2(0xb7883000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x153) = 0xb7883000
mmap2(0xb7886000, 10664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7886000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb772e000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb772e8d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7883000, 8192, PROT_READ)   = 0
mprotect(0x805c000, 4096, PROT_READ)    = 0
mprotect(0xb78be000, 4096, PROT_READ)   = 0
munmap(0xb7889000, 93647)               = 0
getpid()                                = 11080
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x9cbc000
brk(0x9cdd000)                          = 0x9cdd000
getppid()                               = 11079
stat64("/home/joe", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/bin/thunderbird", O_RDONLY)  = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x804f636, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
read(10, "#!/bin/sh\n\n# Firefox launcher co"..., 8192) = 4842
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb772e938) = 11081
close(4)                                = 0
read(3, "/usr/bin/thunderbird\n", 128)  = 21
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 11081
--- SIGCHLD (Child exited) @ 0 (0) ---
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb772e938) = 11082
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 11082
--- SIGCHLD (Child exited) @ 0 (0) ---
stat64("/usr/lib/thunderbird-3.0.6/thunderbird", {st_mode=S_IFREG|0755, st_size=3885, ...}) = 0
stat64("/home/joe/.mozilla-thunderbird", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
lstat64("/home/joe/.mozilla-thunderbird", {st_mode=S_IFLNK|0777, st_size=22, ...}) = 0
stat64("/home/joe/.thunderbird", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
stat64("/home/joe/.thunderbird-3.0", 0xbfdf59d0) = -1 ENOENT (No such file or directory)
stat64("/home/joe/.thunderbird-2.0-replaced", 0xbfdf59b0) = -1 ENOENT (No such file or directory)
lstat64("/home/joe/.mozilla-thunderbird", {st_mode=S_IFLNK|0777, st_size=22, ...}) = 0
stat64("/home/joe/.mozilla-thunderbird", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
execve("/usr/lib/thunderbird-3.0.6/thunderbird", ["/usr/lib/thunderbird-3.0.6/thund"...], [/* 47 vars */]) = 0
brk(0)                                  = 0x87db000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77b2000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=93647, ...}) = 0
mmap2(NULL, 93647, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb779b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000m\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1405508, ...}) = 0
mmap2(NULL, 1415592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7641000
mprotect(0xb7794000, 4096, PROT_NONE)   = 0
mmap2(0xb7795000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x153) = 0xb7795000
mmap2(0xb7798000, 10664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7798000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7640000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb76408d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7795000, 8192, PROT_READ)   = 0
mprotect(0x805c000, 4096, PROT_READ)    = 0
mprotect(0xb77d0000, 4096, PROT_READ)   = 0
munmap(0xb779b000, 93647)               = 0
getpid()                                = 11080
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x87db000
brk(0x87fc000)                          = 0x87fc000
getppid()                               = 11079
stat64("/home/joe", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/thunderbird-3.0.6/thunderbird", O_RDONLY) = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x804f636, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
read(10, "#!/bin/sh\n#\n# ***** BEGIN LICENS"..., 8192) = 3885
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7640938) = 11083
close(4)                                = 0
read(3, "/usr/lib/thunderbird-3.0.6\n", 128) = 27
read(3, "", 128)                        = 0
close(3)                                = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 11083
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7640938) = 11084
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 11084
--- SIGCHLD (Child exited) @ 0 (0) ---
stat64("/usr/lib/thunderbird-3.0.6/run-mozilla.sh", {st_mode=S_IFREG|0755, st_size=10450, ...}) = 0
geteuid32()                             = 1000
getgid32()                              = 1000
getegid32()                             = 1000
getgroups32(0, NULL)                    = 9
getgroups32(9, [4, 20, 24, 29, 46, 104, 115, 120, 1000]) = 9
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7640938) = 11085
wait4(-1, Segmentation fault
[{WIFEXITED(s) && WEXITSTATUS(s) == 139}], 0, NULL) = 11085
--- SIGCHLD (Child exited) @ 0 (0) ---
exit_group(139)                         = ?
```

---

### Post by quixote on 2010-08-27
A complete reinstall and it's still segfaulting?  ??  

If you have virtualbox on your system, you could try installing it in a virtual machine and see whether you still get errors.  Maybe something in your regular installation is conflicting.  Then the error would go away.  Or maybe it's something about your hardware, in which case it might not.

Obviously, I'm clueless too.

---

### Post by escozzia on 2010-08-27
I like the idea of the virtual machine, I think I'll try it soon, and I guess I'll be reporting my results back here.
I doubt it's something with my hardware (that would be really, really weird) because it used to work alright, and it works when I run it as root.

---

### Post by escozzia on 2010-08-28
I think I may have had a bit too much coffee with dinner because I can't sleep
On the plus side I got the virtual box running and installed ubuntu, and yeah, thunderbird works right. So now, time to find out what's wrong with my system I suppose...

---

### Post by quixote on 2010-08-28
That business about it running okay as root means this is all some kind of permissions problem, and the whole segfault error message is just a red herring.  They often are.  I haven't had any coffee yet (6:30 am here), so I'll give this a think and come back.  No ideas off the top of my head, though.

---

### Post by escozzia on 2010-08-28
Alright then, thanks a lot :)
Meanwhile, I'll check some permissions around the system and maybe I'll find something that makes sense

---

