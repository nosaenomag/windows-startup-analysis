 

## Title: Windows Startup and Running Processes Analysis


## Objective

The goal of this analysis is to identify all programs that launch on startup, review running processes, and understand the security implications of persistence. I wanted to check for unfamiliar entries, understand why they might exist, and see how this information can help in defending a system.

## Environment (OS and tools used)

This analysis was done on a Windows 10 64-bit system using a standard user account. I used the Command Prompt with administrative privileges and ran commands such as `tasklist` to view all running processes, `sc query state= all` to check the state of all services, and `wmic startup get caption,command` along with a registry query to examine programs that start automatically.

## Methodology (step-by-step explanation)

I started by opening Command Prompt as administrator. I ran `tasklist` to get a list of all running processes and their memory usage. Next, I ran `sc query state= all` to see all Windows services and whether they were running or stopped. I then reviewed startup entries with `wmic startup get caption,command` and the registry query at `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`. Finally, I compared all entries against known system processes and services to identify anything unusual or unfamiliar.

## Findings

The system has about 12–15 key programs that start automatically, including OneDrive, Surfshark, Teams, and browser auto-launchers like Chrome and Yandex. Most startup entries and running services are familiar and expected. However, some programs, such as “Bible Verse” and Ollama, could be unfamiliar depending on what the user installed. This shows how attackers value persistence, because programs that launch automatically can survive reboots and maintain access. From a defender’s perspective, being able to see startup programs and running services is essential for spotting suspicious activity early.

## Evidence (screenshots embedded inside the document)

I have included screenshots of `tasklist` output showing all running processes and their memory usage. Screenshots from `sc query state= all` display the status of each Windows service. I also included screenshots from `wmic startup get caption,command` and the registry query to show all programs that are set to start automatically. These screenshots back up my findings and make it easier to see which programs are running and which could be unusual.

## Conclusion

This analysis helped me understand how Windows manages startup programs and services, how attackers can use persistence to maintain access, and why defenders need visibility into both running processes and startup entries. The system mostly contains legitimate programs and services, but regular checks for unfamiliar entries are important to ensure nothing malicious is running.

 
