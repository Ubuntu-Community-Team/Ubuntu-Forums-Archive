---
title: "Problema con Squid y sitios de google"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by capitansigfrido on 2011-06-22
Hola.

Les comento mi problema.
Desde ayer estamos teniendo problemas para acceder a google.com o gmail. Otros sitios de internet y de google (por ejemplo google maps) si son accesibles
Podemos acceder a páginas de internet, sean cifradas o no.
La configuración del Squid es la siguiente:

auth_param basic program  /usr/lib/squid3/squid_ldap_auth -v 3 -b "dc=******,dc=com,dc=ar" -f "uid=%s" -h 192.168.1.10 -D cn=admin,dc=*******,dc=com,dc=ar -w *******

external_acl_type ldap_group %LOGIN /usr/lib/squid3/squid_ldap_group -v 3 -b "ou=Egroupware,dc=******,dc=com,dc=ar" -f "(&(cn=%a)(memberUid=%v))" -h 192.168.1.10

acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl red_local dst 192.168.0.0/16
acl ldap-auth proxy_auth REQUIRED
acl https port 443
acl permitidas url_regex "/etc/squid3/permitidas"
acl GPermit external ldap_group InternetAccess
acl SSL_ports port 443 563 8080 873 5223 873 1863 5222
acl Glimitados external ldap_group Limitados
acl gmail dstdomain .gmail.com
acl Prohibidas url_regex -i enlaradio.com.ar radiocolonia.com facebook.com rapidshare.com gustavoeo.net taringa.com taringa.net poringa.com megaporn.com fravega.com garbarino.com musimundo.com radiomitre.com fmrockandpop.com radios-argentina.com.ar rivadavia.com.ar amdelplata.com fmaspen.com radiodisney-ar.disneylatino.com.ar radiouno.com radiouno.com.ar infobae.com youtube.com twitter.com
acl safe_ports port 443 563 8080 873 5223
acl safe_ports port 808

always_direct allow gmail
always_direct allow red_local
cache deny red_local
cache deny gmail

http_access allow manager localhost
http_access allow permitidas
http_access allow red_local
http_access deny manager
http_access deny Prohibidas
http_access deny !Safe_ports
http_access allow localhost
http_access allow GPermit
http_access allow https
http_access deny CONNECT !SSL_ports
icp_access deny all
http_access deny all

http_port 3128
hierarchy_stoplist cgi-bin ?
offline_mode on
cache_mem 32 MB
cache_swap_low 90
cachw_swap_high 95
cache_dir ufs /var/spool/squid3 1000 16 256
access_log /var/log/squid3/access.log squid
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern (cgi-bin|\?)    0       0%      0
refresh_pattern .               0       20%     4320

icp_port 3130
coredump_dir /var/spool/squid3

redirect_program /usr/bin/squidGuard
-----------------------------------------------------------------

Cada vez que intento ingresar a una página de goolge recibo este mensaje en el browser:

While trying to retrieve the URL: [http://www.google.com/](http://www.google.com/) 

The following error was encountered: 

•Connection to 192.168.55.2 Failed 
The system returned: 

    (111) Connection refused
The remote host or network may be down. Please try the request again. 

Your cache administrator is webmaster. 

------------------------------------------------------

En el log del squid veo lo siguiente:

1308717901.950    143 192.168.1.16 TCP_MISS/503 2422 GET [http://www.google.com/](http://www.google.com/) - DIRECT/192.168.55.2 text/html

El error 503 indica por lo que entiendo que no tiene la página en cache y que no pudo conectarse a la misma.
------------------------------------------------------

Si quito el squid en la configuración del browser y salgo directo llego sin problemas. El squid está con una sola placa detrás de un firewall monowall. No tengo habilitado el firewall en este server de momento.

Espero me puedan dar una mano

Slds.

---

### Post by Doregon on 2012-06-25
Hola capitansigfrido:
Si es que navegas con normalidad ¿ya has deshabilitado el ipv6 de tu servidor ubuntu?
A mi me pasaba igual pero con facebook, no me dejaba conectar a mis clientes.
[Aqui]("http://curioseandolinux.blogspot.mx/2010/05/problemas-con-dns-deshabilitar-ipv6-con.html") explican que se debe a problemas con el DNS.

Edita /etc/default/grub
```
sudo nano /etc/default/grub
```y en la parte de GRUB_CMDLINE_LINUX agregas:
```
GRUB_CMDLINE_LINUX=”ipv6.disable=1”
```Recargamos la configuración del grub y reiniciamos:
```
update-grub
reboot
```Con esto me dejó de dar problemas.

Nota: En la mayoria de la información que encuentro, lo ponen en GRUB_CMDLINE_LINUX_DEFAULT, pero yo lo hice en el GRUB_CMDLINE_LINUX.

Fuente: [http://tecnoquia.blogspot.mx/2010/02/deshabilitar-ipv6-en-ubuntu-910.html](http://tecnoquia.blogspot.mx/2010/02/deshabilitar-ipv6-en-ubuntu-910.html)

---

