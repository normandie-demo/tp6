# Correction TP 6


## Modifier l’inventaire pour ajouter une variable `main_service=nginx` au groupe *front*

Editer le fichier *inventory*

```
[front:vars]
main_service=nginx
```

## Modifier le playbook *nginx.yaml* pour démarrer le service provenant de la variable *main_service*

Editer le fichier *nginx.yaml*

```
  - name: Start Service
    ansible.builtin.systemd:
      name: "{{ main_service }}"
      state: started

```

## Exécuter ce playbook sur l’inventaire *inventory*

```Shell
ansible-playbook -i inventory nginx.yaml
```
