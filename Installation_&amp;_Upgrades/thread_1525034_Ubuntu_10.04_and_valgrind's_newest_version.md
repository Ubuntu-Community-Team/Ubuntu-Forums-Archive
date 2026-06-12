---
title: "Ubuntu 10.04 and valgrind's newest version"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by hihihi100 on 2010-07-06
Hi there:

Im pretty sure I have a memory leak problem that has been annoying me since I upgraded to 10.04. I have been told to install Valgrind to check if Im right or not, and I have followed the instructions found at:

[https://wiki.ubuntu.com/Valgrind](https://wiki.ubuntu.com/Valgrind)

The first command worked smoothly. The results for the second command:

```
hihihi100@hihihi100-laptop:~$ rm valgrind.log*
rm: cannot remove `valgrind.log*': No such file or directory

```

which I dont cosnsider to be important, given that that command only deletes the log if it exists, and thats not my case. Please correct me if Im wrong

Now, problems for me appear on the third step:

```
hihihi100@hihihi100-laptop:~$ G_SLICE=always-malloc G_DEBUG=gc-friendly  valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log <program> <arguments>
bash: syntax error near unexpected token `<'

```

Theres no need to add that Im a total noob, and I know nothing about programming, so I would really appreciate if any other user would tell me exactly what do I have to type in the terminal...

RELATED TO THIS:

The amentioned webpage also states that I should (must?) start the program under control of memcheck. I have downloaded a tar.gz file (memcheck-0.2.4.tar.gz), but I dont know what else to do.

Thx

cheers

---

