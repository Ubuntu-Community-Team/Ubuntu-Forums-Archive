---
title: "Copy portions from a text file to another text file"
date: 2006-03-29
forum: Installation &amp; Upgrades
---

### Post by bushtor on 2006-03-29
Hi,

I'm working in text mode only and I wonder if there is an elegant way to copy a portion of a text file to another text file like copyni to / pasting from the clipboard in a gui environment.

Do I have to mark a text block and write it to disk and read it into the other file or do I have faster alternatives?

Thanks for comments

Tor

---

### Post by gnu2tux on 2006-03-29
If you are looking for a way to do it at the command line, then perhaps this will suit:

```


grep -A10 *condition* file >newfile.txt

```

This will look for the word condition, and output that line and the next 9 lines (-A10) below into the file newfile.txt.

So, as long as you know how big your blocks of text are, and they are the same each time, this is very elegant.

If your block sizes are different every time, have a look at cut (man cut).

Regards,

Al.

---

### Post by bushtor on 2006-03-29
Thanks but I need to have two files open at a time and manually (use cursor) select text to copy.  

I basically wondered if there were other ways to preserve a marked portion of text from one open file and paste it into the cursor position of a file open in another text editor.

Sorry for not expressing myself clearly.

Tor

---

### Post by aysiu on 2006-03-29
[QUOTE=bushtor]Thanks but I need to have two files open at a time and manually (use cursor) select text to copy.  

I basically wondered if there were other ways to preserve a marked portion of text from one open file and paste it into the cursor position of a file open in another text editor.[/QUOTE] If I'm understanding you correctly, it sounds as if you all need is Control-C and Control-V.

---

### Post by bushtor on 2006-03-29
[QUOTE=aysiu]If I'm understanding you correctly, it sounds as if you all need is Control-C and Control-V.[/QUOTE]

Does ^C and ^V also work in *text mode* as mentioned in OP?  

I use pico or mc as editors and I hoped to have text files open i different terminals and copy / paste between those, but maybe there is no other way than write to/from disk...

Tor

---

### Post by engla on 2006-03-29
You could also try various shell operations on files with pipes...
This would take the two first lines of file1 and append those to file2.. very rudimentary, but lots of stuff is possible with text-processing utils.
cat file1 | head -n2 | cat >> file2


However, if you use **GNU screen** [a terminal multiplexer, basically hosts multiple shells or other processes in the same tty], you can use its copy buffer. There you can select text and paste it in any of the screen's hosted processes, operated only with the keyboard.

Sample screen usage:
use **screen mcedit file1** at the command line to start a new screen with mcedit editing file1. Now, screen uses the command sequence ^A for all its commands. Type **^A:** inside the running screen to get a : prompt. Type **screen mcedit file2**, and a new hosted mcedit starts. You can switch between the two mcedits with **^A ^N** (n for next) or **^A^P** (p for prev)

Now, in one of those, type **^A Esc** to begin copy buffer mode. Move the cursor to the beginning of the selection, press space. Move the cursor to the end of your selection, press space again and then escape to exit. Type **^A^N** to get to the other editor.. Type **^A:** and then **paste .** (note the dot) to paste in the current window.

---

### Post by aysiu on 2006-03-29
[QUOTE=bushtor]Does ^C and ^V also work in *text mode* as mentioned in OP?  

I use pico or mc as editors and I hoped to have text files open i different terminals and copy / paste between those, but maybe there is no other way than write to/from disk...

Tor[/QUOTE] I don't know the terminal shortcut for *copy* (if I copy from the terminal, I usually have to highlight with my mouse, anyway), so I usually right-click the text to copy. And then to paste, you just press shift-insert.

I don't use pico or mc, but it works for nano.

---

### Post by engla on 2006-03-29
[QUOTE=aysiu]I don't know the terminal shortcut for *copy* (if I copy from the terminal, I usually have to highlight with my mouse, anyway), so I usually right-click the text to copy. And then to paste, you just press shift-insert.

I don't use pico or mc, but it works for nano.[/QUOTE]
In gnome-terminal it's shift+ctrl+C to copy, shift+ctrl+V to paste. However, I understood this question as if this was not in X but in the ttys (alt+ctrl+F1..F6).. I'm still not sure after rereading the thread, though.

---

