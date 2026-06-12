---
title: "Updating Java"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by KaisaUbun2 on 2012-11-02
Hi, so I am having some serious problems updating Java... serious as in it's not working for me... can someone give me an exact step by step. here is as far as I have gotten: 


```
xxx-xxx@xxx-Dell-System-XPS-L702X:~$ sudo -s
[sudo] password for xxx-xxx: 
root@xxx-Dell-System-XPS-L702X:~# cd /home/xxx/Downloads
bash: cd: /home/xxx/Downloads: No such file or directory
root@xxx-Dell-System-XPS-L702X:~# 
```

... I know I have a downloads directory???

---

### Post by KaisaUbun2 on 2012-11-02
wow...okay so I feel pretty stupid, just mispelled the username sorry everyone.

But I'm stuck at the next part now: 

```
xxx-xxx@xxx-Dell-System-XPS-L702X:~$ sudo -s
[sudo] password for xxx-xxx: 
root@xxx-Dell-System-XPS-L702X:~# cd /home/xxx-xxx/Downloads
root@xxx-Dell-System-XPS-L702X:~/Downloads# sudo -s cp -r jdk-7u9-linux-i586.tar.gz /usr/local/java
cp: cannot stat `jdk-7u9-linux-i586.tar.gz': No such file or directory
root@xxx-Dell-System-XPS-L702X:~/Downloads# 
```

ideas? I downloaded the new Java update from Java, and it's in my downloads directory

---

### Post by snowpine on 2012-11-02
The typical method would be to run the Update Manager or the terminal commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by QIII on 2012-11-02
Might I suggest a much, much easier solution that will automatically do updates as they come out?

In the Java wiki in my signature, under "Oracle Java", "Command line methods" is a link "Using webupd8.org's strikingly simple method."

The cleanest, quickest way to install Oracle Java by far.

---

### Post by KaisaUbun2 on 2012-11-02
> **snowpine said:**
> The typical method would be to run the Update Manager or the terminal commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

yup see I tried that, then I pointed the plug-in to Chrome, but the browser is still saying java is not updated...

---

### Post by KaisaUbun2 on 2012-11-02
> **QIII said:**
> Might I suggest a much, much easier solution that will automatically do updates as they come out?

In the Java wiki in my signature, under "Oracle Java", "Command line methods" is a link "Using webupd8.org's strikingly simple method."

The cleanest, quickest way to install Oracle Java by far.

does this also create the symbolic link to the web browser?

---

### Post by snowpine on 2012-11-02
Perhaps your website requires a newer version than Ubuntu provides, for some reason? What is the link? 

QIII's approach looks promising, have you tried that?

---

### Post by KaisaUbun2 on 2012-11-02
> **QIII said:**
> Might I suggest a much, much easier solution that will automatically do updates as they come out?

In the Java wiki in my signature, under "Oracle Java", "Command line methods" is a link "Using webupd8.org's strikingly simple method."

The cleanest, quickest way to install Oracle Java by far.

Thank you this worked, I appreciate it and this saves me a lot of time for the future thank you very much

---

### Post by KaisaUbun2 on 2012-11-02
> **snowpine said:**
> Perhaps your website requires a newer version than Ubuntu provides, for some reason? What is the link? 

QIII's approach looks promising, have you tried that?

I did that worked thank you for your help anyway i appreciate it, updating Java has not been a pain the *** in the past the way I tried earlier but for some reason this update it just didn't want to, thanks though :)

---

