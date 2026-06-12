---
title: "Installation"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by mmanuuec on 2012-06-03
I have a install file install-agraph in folder agraph4.1 and when i write the command 
$agraph4.1 install-agraph destination
for installation

it shows the following error
install-agraph command not found.

So please help me with the solution

---

### Post by codemaniac on 2012-06-03
Helolo mmanuuec ,

Welcome to the UbuntuForums !!

What type of file it is , is it a installer shell script or a binary file or tar.gz .
```
file install-agraph
```
There must be some README available in the directory somewhere , can contain some valuable information on installation .

---

### Post by mmanuuec on 2012-06-03
hey thanks codemaniac for greetings and quick reply.

it is a shell script file but i am not able to find read me file for guidelines.

---

### Post by mmanuuec on 2012-06-03
hey thanks codemaniac for greetings and quick reply.

it is a shell script file but i am not able to find read me file for guidelines.

---

### Post by mmanuuec on 2012-06-03
hey thanks codemaniac for greetings and quick reply.

it is a shell script file but i am not able to find read me file for guidelines.

---

### Post by codemaniac on 2012-06-03
> **mmanuuec said:**
> hey thanks codemaniac for greetings and quick reply.

it is a shell script file but i am not able to find read me file for guidelines.

The execution bit needs to be enable for a shell script so that it can be run .The below command line will make it executable .
```
chmod +x install-agraph
```


Please note that before running the script you can check the contents of the shell script , you can find comments inside that can give you an idea what actually the script does and what are the mandatory options or arguments you need to provide the script for successful execution .

```
./install-agraph
```

---

