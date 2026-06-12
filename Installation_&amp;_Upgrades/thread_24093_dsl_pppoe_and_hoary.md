---
title: "dsl pppoe and hoary"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by vitti on 2005-04-05
Hallo!  :grin: 
Last Friday (1st April 2005) I downloaded HOARY, and than I started installation on my notebook ASUS LD3840. 
For now, for the things that I saw, it seem very interesting, and probably I' ll move also my desktop to UBUNTU.
I have a small home network with one desktop (XP), one MAC mini and the notebook with the new HOARY.
But I found a problem connecting to internet; :? 
For this I use a LAN DSL modem (DHCP server) connected to a LAN switch. and I have  configured pppoe using pppoeconf.
Normally my notebook reach, and it is reached every node of the lan, and the file /etc/resolv.conf contains just one line like this:
"nameserver xxx.xxx.xxx.xxx" (DHCP server address)
When I try to start the internet connection with command:
"pon dsl-provider"
I could see with "Plog" that the connection it was established, and the 2 dns servers from the provider.  :grin: 
At the same time I saw that my /etc/resolv.conf contains just  the 2 DNS addresses, and I suppose that everything was ok.
But when I tried to reach any site on the web with the browser, i got the message that it cannot resolve the url!  #-o  #-o 
Looking at my /etc/resolv.conf,  :-o NOW IT CONTAINS AGAIN JUST ONE LINE! THE ORIGINAL ONE, THE ONE WITH THE DHCP SERVER ADDRESS!
I re-wrote the file with the 2 DNS received, and after a while it was again with just the original ONE line! ](*,) 
It seems that *anyidontknowwhicprocess* (DHCP Client?) every 60 seconds tries, with success!, to overwite the /etc/resolv.conf with the information related to my local LAN, and forgotten the ones received from the provider.
Is there anyone that knows this behaviour? 
May I change in any the DHCP client configuration? :twisted:

---

### Post by Svictor on 2005-04-05
Well, this is not a very elegant solution but it might work. Open /etc/dhcp3/dhclient-script with a text editor and comment this whole function out : 

# make_resolv_conf() {
#   if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
#        local new_resolv_conf=/etc/resolv.conf.dhclient-new
#        rm -f $new_resolv_conf
#
#        if [ -n "$new_domain_name" ]; then
#            echo search $new_domain_name >> $new_resolv_conf
#        else # keep 'old' search/domain scope
#            egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
#                  $new_resolv_conf
#        fi
#        
#        if [ -n "$new_domain_name_servers" ]; then
#            for nameserver in $new_domain_name_servers; do
#                echo nameserver $nameserver >>$new_resolv_conf
#            done
#        else # keep 'old' nameservers
#            egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
#                  $new_resolv_conf
#        fi
#
#        chown --reference=/etc/resolv.conf $new_resolv_conf
#        chmod --reference=/etc/resolv.conf $new_resolv_conf
#        mv $new_resolv_conf /etc/resolv.conf
#    fi
#}

This should stop automatic update of your resolv.conf. Then edit once more the latter with the proper DNS of your provider. There should be 2 of them : 
nameserver xxx.xxx.xxx.xxx
nameserver yyy.yyy.yyy.yyy
Check in System --> Networking that the change was noticed (otherwise, do something, as restarting your connection). This is it. As I said, it's far from being elegant but it should work (I mean, it does for me  ;-) ).

---

### Post by vitti on 2005-04-05
Thanks a LOT! :-D I' ll test your workaround soon and than I' ll give you a feeback!

---

### Post by vitti on 2005-04-05
Thank you Svictor!!
Your quick and very dirty solution works!! 8)   :D 
Now it will be my cure to reproduce this patch at any upgrade, if the new script will not work!

---

