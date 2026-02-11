# Rooting Android

## 1. Fiche Environnement – Périmètre du test

**Application + version :**  
Tests réalisés directement sur le système Android de l’AVD, version 36.1 avec Google APIs (x86_64).

**Support (AVD / device labo) :**  
Émulateur Android (AVD) via Android Studio, modèle Pixel.  
Accès via ADB shell (`emulator-5554`).
![](https://github.com/user-attachments/assets/79a60a72-98ac-4b7a-a822-de044762caff)

**Objectif :**  
Comprendre le processus de rooting sur un AVD et analyser ses impacts sur la sécurité du système.

**Données :**  
Fictives uniquement – aucun compte ou donnée réelle.

**Réseau :**  
Connexion ADB locale (127.0.0.1). Environnement isolé.

---

## 2. Démarrage et installation

- Démarrer un AVD propre  
  ![img7](https://github.com/user-attachments/assets/c45f8fc5-3e29-4d6e-ae4a-a401fb8cc2cc)

- Installer et lancer l'application de test  
  ![img9](https://github.com/user-attachments/assets/79d62aa6-33d3-46e9-b15b-a994c7750501)

---

## 3. Scénarios testés

1. **Ouvrir l’écran d’accueil** – vérifier l’affichage principal  
   ![img10](https://github.com/user-attachments/assets/79d14beb-4612-4c52-854a-5732f3e566b3)  
   ![img11](https://github.com/user-attachments/assets/309307f3-9d89-47a9-a949-1e4723f4ee92)

2. **Rechercher un item** – observer les résultats  
   ![img13](https://github.com/user-attachments/assets/f0cee358-8b66-4b1f-819d-106b3d9d4d10)

3. **Ouvrir un détail (fiche produit/profil)** – vérifier la fiche  
   ![img14](https://github.com/user-attachments/assets/cc7c96b9-6140-4d9a-9f70-de7320cc3bd3)

---

## 4. Sécurité Android

- Chaque app isolée dans sa “boîte”.
- Permissions obligatoires pour certaines fonctionnalités.
- Modifications non autorisées bloquées.
- Protège les données et le système même si root activé.

---

## 5. Verified Boot / AVB

- `getprop ro.boot.verifiedbootstate` → rien sur AVD  
  ![img16](https://github.com/user-attachments/assets/204973f7-d994-4e44-bac1-d631bb035a89)

- AVB (Android Verified Boot 2.0) vérifie l’intégrité et bloque les versions vulnérables  
  ![img17](https://github.com/user-attachments/assets/4c894589-0e00-4b61-97c7-5e1d23469476)

- Sur un vrai appareil : retourne `green`, `yellow` ou `red`.

---

## 6. Rooting

- Droits super-utilisateur sur Android.
- Change les protections et réduit la confiance dans le système.
- Utile en labo pour observer et tester la sécurité  
  ![img8](https://github.com/user-attachments/assets/cd833768-e5b4-4f6c-a1b0-a6c85533c573)
- Toujours travailler isolé et prévoir réinitialisation.

---

## 7. Intérêt en labo

- Accéder à des parties du système normalement invisibles.
- Observer le comportement des applications.
- Vérifier la protection des données sensibles (ex. chiffrement).

---

## 8. Matrice de risques

- Résultats potentiellement faux
- Appareil hors labo, plus exposé aux attaques
- Données sensibles visibles, risque de fuite
- Système instable, tests peu fiables
- Mélange comptes perso/test, risque de fuite d’informations
- Pas de nettoyage, données restantes
- Réseau non isolé, impact possible sur d’autres systèmes

---

## 9. Mesures défensives

- Réseau isolé, appareil dédié
- Données fictives uniquement
- Snapshot/nettoyage après tests
- Journal de configuration et horodatage
- Aucun compte personnel
- Contrôle des APK

---

## 10. OWASP MASVS & MASTG

- **STORAGE-1 :** chiffrer toutes les données sensibles
- **NETWORK-1 :** sécuriser les communications (TLS, certificats)
- Droits root permettent de vérifier le respect de ces exigences.
- Idées de tests basées sur MASTG  
  ![img18](https://github.com/user-attachments/assets/f482b2dd-0410-4f51-81f0-1d8e0036f2db)

---

## 11. Fiche de traçabilité

**Date / Auteur :** 10/02/2026 – Wissal Mokdad  
**Support :** AVD Android Studio, Pixel  
**Version Android / API :** 36.1 (Google APIs, x86_64)  
**Application :** Système Android de l’AVD  

**Scénarios :**  
- Écran d’accueil  
- Recherche d’item  
- Fiche détaillée

**Observations :**  
- AVD stable et tests reproductibles  
- `adb root` fonctionne  
- Verified Boot non disponible sur AVD

**Limites :**  
- Certaines vérifications nécessitent un vrai appareil  
- Tests limités au réseau isolé et AVD

**Reset effectué :** Oui – Snapshot  
![img19](https://github.com/user-attachments/assets/f96b2cef-3822-4ea2-8e53-803b9853f3c2)

---

## 12. Remise à zéro AVD

- AVD réinitialisé après tests  
  ![img20](https://github.com/user-attachments/assets/f42d50cc-8209-4750-ad70-c91dc5520575)

---

## 13. Checklist finale

**Début :**  
- [x] Périmètre écrit  
- [x] AVD neuf  
- [x] App test installée  
- [x] 3 scénarios notés  
- [x] Versions Android/app notées  

**Fin :**  
- [x] Données supprimées  
- [x] Reset effectué (wipe AVD / reset device)  
- [x] Preuve du reset (snapshot)  
- [x] Rapport + traçabilité sauvegardés  
- [x] Aucun compte personnel utilisé
