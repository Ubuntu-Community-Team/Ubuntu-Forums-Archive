---
title: "getting a webserver started"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by ajdphoto on 2005-04-23
Ok, heres the deal, i have a seperate computer that i want to make into a network server for some guys in my dorm.  I have apache started and running.  The problem is this, when i try to install php or mysql it keeps saying that there are no packages.  I update all the packages and i still get the same thing.  I dont really know what todo.  Also, like i said above i have apache working, but i want to make it accessable to people by just typing its name.  example, my dorm is called first east, and i want to people to type in [http://firsteast](http://firsteast) and get to the site.  when i installed ubuntu i figured that would just be the computer name, but now im not sure.  Any help would be appreciated.

---

### Post by myer0052 on 2005-04-23
[QUOTE=ajdphoto]Ok, heres the deal, i have a seperate computer that i want to make into a network server for some guys in my dorm.  I have apache started and running.  The problem is this, when i try to install php or mysql it keeps saying that there are no packages.  I update all the packages and i still get the same thing.  I dont really know what todo.  Also, like i said above i have apache working, but i want to make it accessable to people by just typing its name.  example, my dorm is called first east, and i want to people to type in [http://firsteast](http://firsteast) and get to the site.  when i installed ubuntu i figured that would just be the computer name, but now im not sure.  Any help would be appreciated.[/QUOTE]
 How are you trying to install php and mysql? synaptics? or apt-get install? I think you'd want to install these

apt-get install libapache2-mod-php4  php4-mysql mysql-server

As for setting up the web page so that everyone goes to that address. You could do it by editing the "hosts" file on every computer for that web address to point to your machines IP. 

/etc/hosts:

192.168.1.1     firsteast.dorm.domain    firsteast

That is as long as its only a hand full of machines...

---

### Post by Levander on 2005-04-23
The ubuntu guide has information on installing php, mysql, and apache:

[http://ubuntuguide.org/#apachehttpserver](http://ubuntuguide.org/#apachehttpserver)

It isn't much more than what myer said.  

I would assume the reason it says there are no packages is because you're using the wrong package names?

Also, you need to set up DNS, so that the other computers in your dorm can look up your IP address which their browsers will do when they type the URL of your machine in.  The IP address is how your computer is found on the network.  DNS servers map computer names to these IP addresses. Computers typically are set up to check their own host file, if not found there, it goes to the DNS server they know about.

You can do it like myer said and put host files on all the computers.  Or, you can go to [http://www.dyndns.org](http://www.dyndns.org) and set up an account and register your computer there.

Since your in a dorm, it's possible you'll have a static IP address.  I'm pretty sure dyndns.org supports those.  But, if you've got a dynamic IP address, set every time you connect to the network, then there's an app called ddclient you can set up on your ubuntu box that will keep your ip address updated with dydns.org.

"sudo apt-get install ddclient" if you need that.

---

### Post by ajdphoto on 2005-04-23
>  How are you trying to install php and mysql? synaptics? or apt-get install? I think you'd want to install these

apt-get install libapache2-mod-php4 php4-mysql mysql-server 

synaptics doesnt have anything listed in it regarding php or mysql, and the apt-get comands still are saying "couldnt find package...".  Does apt-get take the proxy settings specified under system->network?  or do i have to add something to a config file to update the list?

About DNS...I looked up the site and that would work, but i dont need this to go outside our campus network.  There already is a simalar site on campus that people just refer to by its computer name.  Can i set up DNS on just my computer?  Thanks for your help!

---

### Post by Levander on 2005-04-23
Are you using hoary?  I don't have a System -> Network menu.  Although I do have a System -> Administration -> Network menu.  However, I don't see anything about a proxy in there.

Not sure if apt-get uses the proxy settings personally, as I've never used a proxy before.

Are you getting any packages at all from apt-get, or just not these couple?  If it's just these couple, then you're probably misspelling them.  Or, it's possible those package are in the universe repositories.  That ubuntu guide link I posted earlier mentions how to enable universe.  It's in the "prerequisite" steps that says "Read How to add extra repositories?".

If you're not getting any packages from apt-get at all, then maybe it is those proxy settings.  Apt-get is configured in /etc/apt/sources.list if you need to look at that.

The machine that all you have to do is enter the name and get to it, that is because it is using the same domain suffix your computer is.  E.g. if one computer is named scratchy.mindspring.com and another is called itchy.mindspring.com, then when your logged into itchy, you can just "ping scratchy".  But, if you're one hello.yahoo.com, you have to "ping scratchy.mindspring.com".  Of course this using the name - and not domain - only works if your computer is set up right.

I believe this can be set up in the DNS server itself.  Where when a computer queries a server for a host's IP, the DNS server can first search in whatever local domain it's set to search in, and if it doesn't find the computer name there, then it tries using the domain name.

And yes, you can set up your own DNS server, you just apt-get (your favorite tool by now) install bind9.  I don't think I found good ubuntu docs on configuring bind9.  Think I ended up using some debian docs.  

However, if you set up your own DNS server, all your friends will have to modify their computers to point at your DNS server.  Or, possibly even a better solution, if your university sysadmins are okay with it, is to ask whoever is administering the DNS server yall are using, if he'll put an entry in there to name your computer?  Then, you most likely will be on the same domain as all the computers that want to connect to it, and they can just enter the name of your computer in their browser like you want.

---

### Post by ajdphoto on 2005-04-23
[QUOTE=Levander]

If you're not getting any packages from apt-get at all, then maybe it is those proxy settings.  Apt-get is configured in /etc/apt/sources.list if you need to look at that.

[/QUOTE]

are you sure its in the sources.list file and not the apt.conf file.  im still looking for the proper syntax for putting a proxy for either of the files.  I found one for the apt.conf file in the AQUIRE branch but it doesnt seem to change anything.  Ill keep trying
thanks for any help.

---

### Post by Levander on 2005-04-23
[QUOTE=ajdphoto]are you sure its in the sources.list file and not the apt.conf file.[/QUOTE]

I just did a quick "man apt.conf" and a "man sources.list".  Apparently, apt.conf is a more general file that configures all kinds of behavior for the "APT suite of tools".  Whereas souces.list is a more specific file that just specifies where to locate archives of packages.

The quick look I did at the man pages, apt.conf is a little confusing to me.  I think there talking about the files in /etc/apt/apt.conf.d when they talk about apt.conf.  I would have to study that man page to really understand.

But, yeah, but from my glancing at it, it does seem like you would configure a proxy in "apt.conf".  Whatever they specifically mean by that.  But, it really sounds like you know more about apt.conf than I, as I had never heard about it until you mentioned it.

I'm not really clear on the whole proxies topic, but I would think that if you can use your computer to get to the internet at all, apt-get should be able to also.  apt-get is just communicating via http.  If your browser can use the system libraries to talk http, I have no idea why apt-get wouldn't be able to use the same libraries to.

---

### Post by crazybill on 2005-04-24
I did not read all of the replies to your answer... so I am sorry if there is any repeated info.

First #cp /etc/apt/sources.list /etc/apt/sources.list_backup  (just to preserver your present list)
Next # edit /etc/apt/sources.list

Replace the contents of the sources.list file with 
[B]deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
[/B]

Next reinstall apache (**apt-get install apache2**) and apache plugins.. such as **apt-get install php4**.  
Then
** /etc/init.d/apache2 restart**

---

### Post by Levander on 2005-04-24
That does look like a pretty good sources.list. However, in the first line in that post that starts with deb-src, the word warty should probably be replaced with hoary.

Also, I asked earlier if ajdphoto was in fact using hoary rather than warty, and never got a response.

That is a sources.list for hoary, not warty.

---

### Post by ajdphoto on 2005-04-24
[QUOTE=Levander]That does look like a pretty good sources.list. However, in the first line in that post that starts with deb-src, the word warty should probably be replaced with hoary.

Also, I asked earlier if ajdphoto was in fact using hoary rather than warty, and never got a response.

That is a sources.list for hoary, not warty.[/QUOTE]
 hey guys i got it all working now, everything, even the DNS.  I am using hoary and i edited the apt.conf file.  You have to insert this

 Http {
        Proxy "http://user: [email]pass@proxy.domain.com[/email]: port";/
   }

in the aquire portion of the file.

after that i just went to apt-get.org and found the sources that i needed in order to get php and such, and now i have it all installed. 

thanks for all your help

---

