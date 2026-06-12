---
title: "Microsoft proxy"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by chk9 on 2005-11-30
We're using a Microsoft Proxy server and I'm unable to update the package listing.
I've searched through all the proxy issues I could find, but all to no avail.

I could not get **apt-get** to work with either:

_/etc/apt/apt.conf :_
Aquire::http::Proxy "http://mydomain\myid:mypsw@my.proxy:8080";

or
_/etc/apt/apt.conf :_
AQUIRE {
  http {
    Proxy "http://my.proxy:8080";
  };
};
Debug 
{
  Acquire::Http "true";   // Show http command traffic
}


apt-get never directed it's http traffic the the proxy server, but went always after 82.211.81.138 and 216.165.129.138 directly.

I'v also tried the **Synaptic Package Manager**.
I've set Settings->Preferences->Network to use the proxy either with:
http: my.proxy:8080
http: mydomain\myid@my.proxy:8080
http: mydomain\myid:mypsw@my.proxy:8080

The last setting came close to working, but it only wanted to do "Proxy-Authentication: **Basic"**
and the server requires either "Proxy-Authentication: **Negotiate**", "Proxy-Authentication: **Kerberos**" or "Proxy-Authentication: **NTLM**"

I'v also configured _System->Preferences->Network Proxy_...

On a good note Firefox does work and this posting is from my Breezy system :-)

Thanks for helping,
A puzzled new Ubuntu user (Chris) ](*,) .

---

### Post by seismicmike on 2005-12-01
Dude, I don't know for sure exactly what to tell you, all I know is that by reading your post, I figured out my problem... I'm thinking we both have pieces of the puzzle and we needed the other... Maybe if you read my post, you can figure out what's wrong with yours?

[Here's my thread.]("http://www.ubuntuforums.org/showthread.php?t=96802")

---

### Post by chk9 on 2005-12-02
Thanks seismicmike,

[This message had my answer !]("http://www.ubuntuforums.org/showthread.php?p=533842#post533842") :-D

To quote the giste of it:
> OK, I got it. You are trying to authenticate against a MS ISA proxy. If it is using NTLM authentication, you are not going to get very far.

I had this problem at work. In order to get around it, I used this neat little python script that acts as a proxy to the proxy, and it can do NTLM authentication on your behalf.

You can get the script here: [http://www.geocities.com/rozmanov/ntlm/](http://www.geocities.com/rozmanov/ntlm/)


Install was a breezy ;-)
Off to play now.... :KS

---

