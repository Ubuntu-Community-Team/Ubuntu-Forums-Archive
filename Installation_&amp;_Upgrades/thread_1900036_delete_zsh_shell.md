---
title: "delete zsh shell"
date: 2011-12-25
forum: Installation &amp; Upgrades
---

### Post by kerasi on 2011-12-25
Hi
i have removed zsh shell before go back to bash now i dont have a shell that works what can i do?

i hope i dont have to install lubuntu new

and marry christmas to all

---

### Post by Lars Noodén on 2011-12-25
You can remove zsh and reset your login shell like this:

```

sudo apt-get remove zsh
sudo usermod --shell /bin/bash *kerasi* 

```

---

### Post by kerasi on 2011-12-25
hi
where should i type this my xterm dont work

---

### Post by Stanley_00 on 2011-12-25
I think you should use recovery mode to reset your login shell.

---

### Post by kerasi on 2011-12-25
great it works :-)

but when i will log in as

shaft ~ $ sudo -i
sudo: shell: command not found

here is my passwd

> root:x:0:0:root:/root:/bash/shaft
shaft:x:1000:1000:John Shaft,,,:/home/shaft:/bin/bash

maybe i did an mistake in my dilirium of anger :-(

---

### Post by kerasi on 2011-12-25
i found my mistake :-)))

root:0:0:root:/root:/bin#i forgot/bash/shaft

coool many many thanks

---

