---
title: "Installing Java"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by robinpaschal on 2010-09-17
Hello to all..


[LIST]
[*]I want to install Java...? Where can i download and can anybody tell me how can i install it?
[/LIST]

[LIST]
[*]I have one more doubt. I am using two browser with Ubuntu. I want to install software ( informenter in chrome). Is this possible to install it
[/LIST]
I already download informenter.xpi from web...But still facing problem to install it.

---

### Post by arjunbajaj on 2010-09-17
Hey...

to install Sun Java 6 JDK just open terminal and type :

```
sudo apt-get install sun-java6-jdk
```

and press enter

it will start installing


thats it.....

---

### Post by lykeion on 2010-09-17
OP is asking how to install Java. Then he's asking about some xpi plugin for chromium.
It's obvious he's not asking about the Java Development Kit (JDK) like above poster suggests.
What he's asking for is the Java browser plugin.

Firefox
Enter "about:plugins" in the address field to check installed plugins. You should see a Java plugin entry. 
By default the IcedTea (OpenJDK) plugin is installed. Some web pages will complain if not the Sun Java plugin is found and say "Please install Java". 

To remove IcedTea and install Sun Java plugin:

1) Enable partner repository:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

2) Start synaptic and:
remove icedtea6-plugin package
install sun-java6-plugin

3) Restart browser

Chromium (aka Google Chrome)
I don't use this browser myself so you should google/search this forum for something like "chromium java plugin".

---

