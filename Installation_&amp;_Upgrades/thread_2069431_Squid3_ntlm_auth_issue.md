---
title: "Squid3 ntlm_auth issue"
date: 2012-10-10
forum: Installation &amp; Upgrades
---

### Post by pstonge on 2012-10-10
Hey guys, I have checked, and checked, and checked, and i cant seem to find the solutions to my problem. 

My setup is, Ubuntu Server 12.04 with Squid3, Winbind, Samba, Kerberos, with adzapper. Our domain is Windows Server 2003, and I have joined the domain, i can list the users and groups with wbinfo -u amd -g. I can get on the internet, and see the zapped addes (without uncommenting the auth_param), because when I do, I lose my internet connection. I am having an issue with this one line.
 
auth_param ntlm program <helper program location><helper program switches>
 
When I look online it says to use;
 
                                              /usr/lib/squid3/ntlm_auth
 
For the <helper program location> problem is i have no such file in squid3. 
 
Also I seen online to use;
 
                                            --helper-protocol=squid-2.5-ntlmssp
 
For the <helper program switches> Is that, something that is automatically used or something, because first of all i have no file with squid-2.5 or ntlmssp. And second I am using Squid3.
 
I read that the Samba ntlm_auth should be used instead of Squid, but I do not have a Samba ntlm_auth file either. 
 
I am kinda stuck at this point, not too sure what to do. Any help would be appreciated.
 
Thanks Paul

---

