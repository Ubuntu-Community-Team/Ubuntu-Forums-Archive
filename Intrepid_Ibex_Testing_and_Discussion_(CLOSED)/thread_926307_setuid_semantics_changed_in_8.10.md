---
title: "setuid semantics changed in 8.10?"
date: 2008-09-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LarryHastings on 2008-09-21
*(Manually crossposted from Main Support Categories | Security Discussions.)*

I've been using Ubuntu as my daily OS since 7.04.  I have to use the Juniper VPN software for work, which includes "ncsvc", a setuid program to drive the tun virtual network device.  This worked fine until I got to 8.10.

I eventually figured out the first piece of the puzzle: the semantics of setuid seem to have changed for 8.10.  It seems that 8.10 requires setuid programs to be readable as well as executable.  I changed ncsvc from 711 to 755 and it got past that problem.  (It still doesn't work, sigh, but that's a question for another day.)

Here's a test case.  I compiled the following program, uid.c:```
#include <stdio.h>
#include <string.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
  FILE *f;
  char buffer[256];
  sprintf(buffer, "Hello there, I'm uid %d, euid %d.\n", getuid(), geteuid());
  puts(buffer);
  f = fopen("foo", "wt");
  fwrite(buffer, 1, strlen(buffer), f);
  fclose(f);
  return 0;
}
```I then "sudo bash" and run```
# chown root ./uid
# chgrp root ./uid
# chmod 711 ./uid
# chmod u+s ./uid
# chmod g+s ./uid
# ls -l ./uid
-rws--s--x 1 root root 9346 2008-09-19 12:34 ./uid

```
I then exit from the su'd bash shell and run "% ./uid".

If I'm on 8.04, it prints out "Hello there, I'm uid 1000, euid 0.".  If I'm on 8.10, I get an error message: "zsh: permission denied: ./uid".

If I su again and make it 755:```
# chmod 755 ./uid
# chmod u+s ./uid
# chmod g+s ./uid
# ls -l ./uid
-rwsr-sr-x 1 root root 9346 2008-09-19 12:34 ./uid

```then I can run it as myself and it works.

I'm a bit surprised by this.  I figured the semantics of setuid were pretty well set in stone by now.  Why did this change?

---

### Post by Yannick Le Saint kyncani on 2008-09-21
> **LarryHastings said:**
> "zsh: permission denied: ./uid".

Hi LarryHastings, could you try with bash instead of zsh ?

---

### Post by LarryHastings on 2008-09-22
> **Yannick Le Saint kyncani said:**
> Hi LarryHastings, could you try with bash instead of zsh ?Here you go:```
$ ./uid
bash: ./uid: Permission denied
```

And, before you ask, here it is executed from Python:```
$ python
Python 2.5.2 (r252:60911, Sep 14 2008, 10:31:08) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import subprocess
>>> subprocess.call("./uid")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/subprocess.py", line 444, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1153, in _execute_child
    raise child_exception
OSError: [Errno 13] Permission denied
>>>
```

---

