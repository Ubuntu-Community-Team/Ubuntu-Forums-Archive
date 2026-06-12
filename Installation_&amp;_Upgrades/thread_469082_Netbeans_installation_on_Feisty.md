---
title: "Netbeans installation on Feisty"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by aerotops on 2007-06-09
I am having trouble installing Netbeans on Feisty. I think the reason has something to do with the size of my /tmp folder.  I understand that /tmp is like any other folder, so it really should not be a problem.

I have about 60MB free space in my tmp folder. My Netbeans install is about 160 MB. The install always fail with a message about the size of my tmp folder. Any pointers as to how to resolve this will be appreciated.

---

### Post by madmetal on 2007-06-10
> **aerotops said:**
> I am having trouble installing Netbeans on Feisty. I think the reason has something to do with the size of my /tmp folder.  I understand that /tmp is like any other folder, so it really should not be a problem.

I have about 60MB free space in my tmp folder. My Netbeans install is about 160 MB. The install always fail with a message about the size of my tmp folder. Any pointers as to how to resolve this will be appreciated.

why just dont try 
sudo aptitude install netbeans
? it would install netbeans proper ;)

---

### Post by Vola on 2007-06-10
the apt-get install for netbeans requires that you place manually a tar.gz into tmp folder. I think this is a quite stupid thing...

anyway aerotops, you can make a symlink to the tar

---

### Post by aerotops on 2007-06-10
Thanks for the replies. I was able to install Netbeans 5 through synaptic, thanks for the tip. It never occurred to me :-)

My next question would be about the symlink mentioned above. I will read about it online and try it out. But is there a short description or a step by step on how to use them. I am only asking because I would like to get developing sooner rather than mucking around in online tutorials. So, if there's a quick and easy way, I would appreciate it very much.

---

### Post by Vola on 2007-06-11
Ok, you can make a symbolic link into tmp that points to the real file.

On the console:

move on tmp:

```
cd /tmp
```          

make a symbolic link:

```
ln -s /home/user/pathToNetbeans.tar.gz  netbeans.tar.gz
```         

where path to netbeans is where real file is and netbeans.tar.gz is the file synaptic needs (change the name as you need!!) 

maybe needs also root owner:

```
chown root.root netbeans.tar.gz
```

this makes a "fake" file thas links the real file.

In this way you can leave the netbeans tar on another location without use /tmp/ space

---

