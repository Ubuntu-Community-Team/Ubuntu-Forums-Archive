---
title: "Synergy linux/windows issue."
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by toarlach on 2008-11-06
I'm trying to get synergy working on my Windows machine from my Linux box which will be the server. I have synergy running with the /etc/synergy.conf file below... To run synergy, I run synergys

csweely is my linux box and chad is my windows box. Both can ping/traceroute to one another with no issues.

```
section: screens
csweely:
chad:
end

section: aliases
chad:
192.168.1.66
end

section: links
csweely:
right = chad
chad:
left = csweely
end

```

I have Synergy running on my Windows box and have 'Use another computers shared keyboard and mouse (client)' checked with the other computer's hostname (csweely) in the text box. When I click start, the error log comes up saying "The attempt to connect was forcefully rejected". 

To troubleshoot, I have also tried the IP in the 'Other computer' section on Windows. I just don't know what is going wrong--they both can see each other if I ping the other one. 

Any help would be appreciated.

---

### Post by blazerw on 2008-11-06
"Forcefully rejected", how rude!
Some questions:

Do you have a firewall running on your Linux box? Do
```
iptables --list
```

Do you have a firewall on the Windows box that is preventing outgoing connections from Synergy?

You might try installing "quicksynergy" on the Linux box for easier configuring. It's a nice GUI.

Also, since Linux is the server, you don't really need the aliases section, just put:
```
192.168.1.66     chad
```
in your /etc/hosts file.

Hope that helps.

---

### Post by toarlach on 2008-11-12
Here's the results from the iptables --list
> 
csweely@csweely-desktop:~$ sudo iptables --list
[sudo] password for csweely: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
csweely@csweely-desktop:~$ 

---

### Post by zarthon on 2008-11-22
Upgrading to 8 broke my quicksynergy connection to my windows xp laptop as well. It is clearly on the Ubuntu side of things where something was broken.
Could it be /etc/services ?? 
I updated /etc/hosts/allow
Did you get this working?

---

