---
title: "Commandline tail -r"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by Surfer-07 on 2009-12-05
Hello everybody,

I'm having a problem using the command line.

For some script I need the "tail -r" command but in the new version of the command the -r option isn't available anymore.

Is it possible to downgrade the tail command or is there any alternative?

Grtz ;)

(I'm using Ubuntu 9.10 64bit)

---

### Post by phillw on 2009-12-05
Hi,

what did the -r option used to do ?

Phill.

---

### Post by lswb on 2009-12-05
I see that the version of tail on BSD systems includes the -r option. Looks like the GNU version does not.

Something like this will have the same effect:
```

tail filename|cat -n|sort -nr|cut -f2

```

---

### Post by Surfer-07 on 2009-12-05
> **phillw said:**
> Hi,

what did the -r option used to do ?

Phill.

Option '-r' stands for reverse. It puts the file content upside down.

For example:

bash~$ cat Test.txt
Line1
Line2

bash~$ tail -r Test.txt
Line2
Line1
 
> **lswb said:**
> I see that the version of tail on BSD systems includes the -r option. Looks like the GNU version does not.

Something like this will have the same effect:
```

tail filename|cat -n|sort -nr|cut -f2

```

That also works. You can even make it shorter:
cat -n filename | sort -nr | cut -f2 ;)
But is there no other alternative?

Grtz

---

### Post by Surfer-07 on 2009-12-05
I just found the solution.
There is a "tac" command that works great :)
just use bash:$ tac Test.txt

---

