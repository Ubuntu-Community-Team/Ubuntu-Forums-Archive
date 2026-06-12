---
title: "Install a software with a .sh file"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by skalettt on 2011-05-07
Hi! 
A friend gave me a *.sh* file through which I should install a commercial software. 
How can I run this file in order to install the software?
Could someone give me further information about *.sh* file?
Thank you vm!

---

### Post by matt_symes on 2011-05-07
Hi

> **skalettt said:**
> Hi! 
A friend gave me a *.sh* file through which I should install a commercial software. 
How can I run this file in order to install the software?
Could someone give me further information about *.sh* file?
Thank you vm!

Can you tell us the name of the software ?

Generally to install via a .sh file you will be looking to type something like (at the terminal)

```
sudo /path/to/scrip.sh
```

However, to know exactly what to do, it would be useful if you could tell us the name of the software package you are trying to install.

Also, is there a README file with the software ? That will generally have installation instructions.

Kind regards

---

### Post by skalettt on 2011-05-07
I don't have any README file.. the software is a popular software for CFD 
(computation fluid dynamics) analisis. 
I tried to execute the *.sh* file with the instructions you've attached to me in your previous email;
I wrote

*sudo /path/to/*NameOfFile.sh

but "command not found"

---

### Post by matt_symes on 2011-05-07
Hi

> sudo /path/to/NameOfFile.sh

Exactly what did you type here ? In which directory is the file ? What is your current directory ?

If you are in the same directory as the file you will need to type (notice the dot)

```
sudo ./name_of_file.sh
```

If you are in another directory, use the full path to the directory to be sure.

```
sudo /path/to/directory/name_of_file.sh
```

Kind regards

---

### Post by sisco311 on 2011-05-07
Assuming that the path is correct, you either set the executable bit of the file before you run it:
```
chmod +x /path/to/file.sh
sudo /path/to/file.sh
```
or explicitly specify the interpreter:
```
sudo sh /path/to/file.sh
```

If you are unsure about the path to the file, simply type **sudo sh** then an extra space and drag and drop the file in the terminal window.

---

### Post by matt_symes on 2011-05-07
Hi

@sisco311.

Hmmmm. You've stolen my thunder.

```
chmod +x /path/to/file.sh
```

That was going to be my next suggestion.

Good luck on the application.

Kind regards

---

### Post by dino99 on 2011-05-07
> **skalettt said:**
> I don't have any README file.. the software is a popular software for CFD 
(computation fluid dynamics) analisis. 
I tried to execute the *.sh* file with the instructions you've attached to me in your previous email;
I wrote

*sudo /path/to/*NameOfFile.sh

but "command not found"

of course customise with your: path of file's name :(

---

### Post by skalettt on 2011-05-07
Thank you everybody!
I could actually install the CFD software! 
..but now I have a matrioska of folders and files.. 
Of course I expected it, but I would need to access to the graphic interface of the 
software. How can I do it?
I used to work with this software with an icon on the Desktop, and double-clicking on it
I could access to the graphic interface of the software.
But now?

---

