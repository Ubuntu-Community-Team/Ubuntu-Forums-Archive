---
title: "Installing .bin file"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Ceiber Boy on 2010-10-12
Trying to install .bin file

these are the commands i'm using 

chmod a+x NameOfFile.bin
./NameOfFile.bin

it responds with 

./NameOfFile.bin: No such file or diectory

it is a 64 bit bin for a 64 -bit system so i dont know whats going on!

i'm tryint to install acrobat reader can anyone help please

---

### Post by Slim Odds on 2010-10-12
> **Ceiber Boy said:**
> Trying to install .bin file

these are the commands i'm using 

chmod a+x NameOfFile.bin
./NameOfFile.bin

it responds with 

./NameOfFile.bin: No such file or diectory

it is a 64 bit bin for a 64 -bit system so i dont know whats going on!

i'm tryint to install acrobat reader can anyone help please

Sounds like maybe a typo?

Why don't you just add the third party repositories and install it from there?

---

### Post by akoskm on 2010-10-12
> **Ceiber Boy said:**
> Trying to install .bin file

these are the commands i'm using 

chmod a+x NameOfFile.bin
./NameOfFile.bin

it responds with 

./NameOfFile.bin: No such file or diectory

it is a 64 bit bin for a 64 -bit system so i dont know whats going on!

i'm tryint to install acrobat reader can anyone help please

```

chmod +x NameOfFile.bin
sh NameOfFile.bin

``` should work.

---

### Post by Slim Odds on 2010-10-12
> **akoskm said:**
> ```

chmod +x NameOfFile.bin
sh NameOfFile.bin

``` should work.

+x   is the same as  a+x

sh NameOfFile.bin   is the same as ./NameOfFile.bin

---

### Post by Ceiber Boy on 2010-10-27
I did h whole load of updates and and bingo it took!

cant explain why but glad its solved.

Thanks for you comments.

---

