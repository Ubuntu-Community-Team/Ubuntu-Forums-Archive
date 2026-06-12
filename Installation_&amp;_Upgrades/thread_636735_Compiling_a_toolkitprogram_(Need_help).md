---
title: "Compiling a toolkit/program (Need help)"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by iMMo on 2007-12-10
Hi,
As you may have noticed, im not new that new to the board but it is my first post. So i will take this opportunity to give the community the big thumbs up, which without, a lot of us would probably die of frustration or just migrate back to windows.
:):):)

I normally search the board for solutions and it has always helped until now, hence my first post. And only because of my cluelessness when it comes to programming/compiling, ect.

I am having difficulties trying to install/compile this certain program which i need for my work.
[http://sbe.napier.ac.uk/~manuel/epanetlinux](http://sbe.napier.ac.uk/~manuel/epanetlinux)
I have read through the entire page and still could not produce the program.

the line :
$ gcc -I./toolkithdir/ -o yourprogram yourprogram.c libtoolkit.a -lm
is very alien to me and I have tried changing various parameters but no outcome.
I also understand that I may have to produce a myprogram.c file which has the mentioned header of: 
#include "toolkit.h" ..... but is there more to this?
:confused::confused::confused:

I am running ubuntu gutsy 64bit.

Please help.

Thanks in advance.

---

### Post by Jussi Kukkonen on 2007-12-10
"toolkit" here means a  library, something you use in your own program (yourprogram.c in the example). Since gcc invocation is alien to you, I guess you are not developing a program... What are you trying to accomplish?

---

### Post by iMMo on 2007-12-10
In short, I need EPANET to work on Ubuntu.

But from what I gathered, I may need to write my own program, with header

[COLOR="Green"]#include "toolkit.h"[/COLOR]

Apart from just adding the line #include "toolkit.h" in my own .C file, i dont know where to go from there.

P.S. I realised this topic is in the wrong section, apologies.

---

