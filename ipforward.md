Your Scenario
You have a Raspberry PI or any linux distro device (nowonwards it will be referred to as DEVICE) which has Wifi and LAN port.
You have clients connected to your DEVICE and the DEVICE is connected to your existing LAN network or WIFI router.
Now you need to share your raspberry-pi's internet to other WiFI users


sudo sysctl -w net.ipv4.ip_forward=1

(This is assuming that your wifi is on wlan0) (If you dont know, then dont worry, by default it Wifi in pi is wlan0)
sudo iptables -A FORWARD --in-interface wlan0 -j ACCEPT

(This is assuming your LAN is eth0, if you want to confirm that once, then type ifconfig before typing below command)
sudo iptables --table nat -A POSTROUTING --out-interface eth0 -j MASQUERADE

Now give the ip of this DEVICE as a gateway to all your wifi clients.
