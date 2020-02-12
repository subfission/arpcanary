ARP Canary
=========

ARPCanary monitors for ARP protocol spoofing attacks.  These are typically precursers to a man-in-the-middle attack.


The script is easy to set up and safe to run in background. Once an ARP spoof attack is detected, a system notification will be sent to the user, and corresponding information will be logged in the log file.


Features
----
  - Detect ARP reply messages in the network.
  - Detect if a machine has launched ARP spoof attack in the network.
  - Log all ARP reply messages and potential ARP spoof attacks in the log file.
  - Send system notification to user once such attack occurs. (Currently only supported in Mac OS X)

Dependencies
-----------
ARP Spoof Detect requires the following two packages to function on any machines.

* [Scapy] - Powerful packet manipulation package.
* [Netifaces] - Python network interface reader.

On Ubuntu machine, it is easy to install these two packages by doing
```
apt-get install python-scapy python-netifaces
```
On Mac OS X, use pip to install scapy and netifaces.
```
pip install -r requirements
```

How To Run
----
```
$ sudo ./arpcanary -i INTERFACE
```
Root privilege is required to operate network interfaces.


Example
```
$ sudo ./arpcanary --log spoof.log -i en0

ARP Spoofing Detection Started. Any output is redirected to log file.
```

If you are running Mac OS X, when an ARP spoofing attack is in the network, you will receive a system notification alerting you to take proper actions. Otherwise, the attack will be logged in the log file. You may implement a listener that watches the file for the attack, should you need a realtime notification. 

[Scapy]:http://www.secdev.org/projects/scapy/
[Netifaces]:https://pypi.python.org/pypi/netifaces

Virtual Env Setup Example
----

From inside the arpcanary directory, run:
``` 
virtualenv -p /usr/local/bin/python3 .env
source .env/bin/activate
pip install -r requirements.txt
```
