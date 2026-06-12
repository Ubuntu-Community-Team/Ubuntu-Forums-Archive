---
title: "How do i install Java???"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by alex98uk on 2008-05-08
Hello, i'm relatively new to Ubuntu. I have used Linux for a while day to day, but have never really got down and dirty with it yet.

Basically, my issue is that i am unable to install Java, and thus Firefox cannot display any page using Java.

I downloaded the latest Java installer (jre-6u5-linux-i586.bin), it is from here i get stuck. It says on the site to type "su" into the terminal and log in. However, i do this and use my standard login password but i get a: "su: Authentication failure".

It looks like i'm not the actual owner because i am unable to copy any files into the root directory. So, first, how do i become the owner and have access to root.

Secondly, how do i go about installing this Java package?

I'm pretty simple, so take it easy on me if i don't understand :)

Cheers

---

### Post by Ponhovo on 2008-05-08
"I downloaded the latest Java installer (jre-6u5-linux-i586.bin), it is from here i get stuck. It says on the site to type "su" into the terminal and log in. However, i do this and use my standard login password but i get a: "su: Authentication failure"."

Secondly, how do i go about installing this Java package?

it's sudo 
you  can install it by typing on the terminal:
sudo chmod 777 jre-6u5-linux-i586.bin
./jre-6u5-linux-i586.bin

"So, first, how do i become the owner and have access to root."

you can log in as root b typping:
sudo -i

then you enter your password, but you canm also typo "sudo" before typing a command line, it works too

---

### Post by alex98uk on 2008-05-08
Cheers, that worked.

I did it before however, what's confusing me is that the test Java applet on java.com's website doesn't show correctly, yet i have java and javascript turned on in firefox and when i type in about:plugins, it displays properly.

---

