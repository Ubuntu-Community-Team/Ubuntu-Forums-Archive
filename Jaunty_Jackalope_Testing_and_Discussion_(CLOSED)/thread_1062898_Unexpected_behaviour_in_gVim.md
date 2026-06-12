---
title: "Unexpected behaviour in gVim"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nairobiny on 2009-02-07
Hi there.

I'm new to Ubuntu, but have a decent amount of experience of using other distros, mostly for server purposes, on other computers.  Currently I'm running jaunty on a Dell XPS M1330.  And I'm having some trouble with gVim.

This is vim-gnome that was installed via apt-get.  It's not behaving the way I would expect it to.  The biggest problem is that it keeps jumping into insert mode when I don't want it to.  For example, if I go into visual mode (shift V to select a line) and then try to yank or delete that line, it inserts the command ("y" or "d") over my highlighted text, instead of sticking that text into a register.  To get it to work the way I expected it to, I have to do a ctrl-L before hand to tell it to get out of insert mode.

I have "set noim" in my .vimrc.

I don't think it's meant to behave like this.  vim doesn't do this on my other linux box, or on the gVim I have used before on windows.

Can anyone help me get it working properly or shed any light on what might be going on?

---

### Post by nairobiny on 2009-02-09
I found the answer:

In .vimrc I changed:
```
set selectmode=mouse,key,cmd
```

to:
```
set selectmode=mouse,key
```

Now it behaves itself.:D

---

