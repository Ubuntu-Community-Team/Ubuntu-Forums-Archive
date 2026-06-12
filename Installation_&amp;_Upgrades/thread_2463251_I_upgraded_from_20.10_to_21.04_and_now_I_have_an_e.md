---
title: "I upgraded from 20.10 to 21.04 and now I have an error..."
date: 2021-06-07
forum: Installation &amp; Upgrades
---

### Post by denddyprod on 2021-06-07
Hello everybody,

I have successfully upgraded a new version of Ubuntu 21.04 and now when press the button to add a new terminal, I have an error : 

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.


bash: /.cargo/env: No such file or directory

Please help me to solve this problem...

Thank you in advance!

---

### Post by grahammechanical on 2021-06-07
The first statement about needing to use "sudo" when running commands as administrator is standard advice that appears the very first time we open a terminal. It will not appear the next time the terminal is opened. It is a distraction. This is the actual error message:

> bash: /.cargo/env no such file or directory:

I cannot help you with this error message. What are you expecting to happen?

Regards

---

