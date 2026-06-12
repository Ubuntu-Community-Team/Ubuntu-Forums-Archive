---
title: "byobu segfaulting in natty"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by danielschonfeld on 2011-05-24
I've just installed byobu on my natty 11.04 using apt-get and for some reason when I try to run it with "-d" or "-D" and issue a command it segfaults.

for instance

#: byobu -D -m top
Segmentation Fault

strace reveals:

fstat(3, {st_mode=S_IFREG|0644, st_size=1626, ...}) = 0
mmap(NULL, 1626, PROT_READ, MAP_SHARED, 3, 0) = 0x7f4cbf7de000
lseek(3, 1626, SEEK_SET)                = 1626
munmap(0x7f4cbf7de000, 1626)            = 0
close(3)                                = 0
open("/etc/shadow", O_RDONLY|O_CLOEXEC) = -1 EACCES (Permission denied)
umask(0)                                = 022
stat("/var/run/screen", {st_mode=S_IFDIR|0775, st_size=80, ...}) = 0
fstat(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4cbf7de000
write(1, "Directory '/var/run/screen' must"..., 49Directory '/var/run/screen' must have mode 777.
) = 49
exit_group(1)                           = ?

Ideas?

---

