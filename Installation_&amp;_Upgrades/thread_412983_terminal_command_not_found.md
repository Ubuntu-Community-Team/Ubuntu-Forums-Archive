---
title: "terminal command not found"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by alfreddo on 2007-04-18
Looking at 'The Official Ubuntu Book' section entitled 'crash Course in the Terminal', it suggests first looking at the files in your home folder by running this command in the Terminal:

foo@bar~$ 1s

But when I then press enter, I get this message:

foo@bar~$ :  command not found.

As foo@bar~$  seems to precede most commands I find myself stuck on the first step.

Am I missing something?

---

### Post by yabbadabbadont on 2007-04-18
The command is lowercase "LS", not "1s".  :)

---

### Post by spd106 on 2007-04-18
dir will also work

---

### Post by alfreddo on 2007-04-18
I'fe just tried both ls and dir, but I think the problem occurs with the first part of the command. After pressing enter I get this message:

bash: foo@bar~$ : command not found

---

### Post by spd106 on 2007-04-18
No, no "foo@bar:~$ " is the prompt, like "C:/>" except it says your username and your computer's host name.

So in the example given
foo = username
bar = hostname
~ = path to the working directory, currently your home directory
$ = the prompt symbol, like > (it changes to a # when you are root)

Just enter the command after the $, and you should be ok.

---

### Post by alfreddo on 2007-04-18
Aha!  That makes more sense - I was still thinking in Windows terminology.

But I think page 142 in The Official Ubuntu book needs clarifying for newbies such as myself. Perhaps SPD106's explanation could be included in a future update?

Thanks. I shall plod on.

Alfreddo

---

